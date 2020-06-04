---
title: init_seg (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221008"
---
# <a name="init_seg-pragma"></a>init_seg (Pragma)

**C++Cuestión**

Especifica una palabra clave o una sección de código que afecta al orden en que se ejecuta el código de inicio.

## <a name="syntax"></a>Sintaxis

> **#pragma init_seg (** {**usuario** **lib** |  **del** | compilador | "*section-Name*" [ **,** *FUNC-Name* ]} **)**

## <a name="remarks"></a>Comentarios

Los términos *segmento* y *sección* tienen el mismo significado en este artículo.

Dado que a veces se requiere código para inicializar objetos estáticos globales, debe especificar Cuándo se deben construir los objetos. En concreto, es importante usar la pragma **init_seg** en bibliotecas de vínculos dinámicos (dll) o en bibliotecas que requieran inicialización.

Las opciones de la pragma **init_seg** son:

**compilación**\
Reservada para la inicialización de la biblioteca en tiempo de ejecución de C de Microsoft. Los objetos de este grupo se construyen en primer lugar.

**obj**\
Disponible para las inicializaciones de los proveedores de bibliotecas de clases de terceros. Los objetos de este grupo se construyen después de losmarcados como compilador, pero antes de cualquier otro.

**usuario**\
Disponible para cualquier usuario. Los objetos de este grupo se construyen en último lugar.

*nombre de sección*\
Permite la especificación explícita de la sección de inicialización. Los objetos de un nombre de *sección* especificado por el usuario no se construyen implícitamente. Sin embargo, sus direcciones se colocan en la sección denominada por *section-Name*.

El *nombre de la sección* que se proporciona contendrá punteros a funciones auxiliares que construirán los objetos globales declarados después de la instrucción pragma en ese módulo.

Para obtener una lista de los nombres que no se deben usar al crear una sección, vea [/section](../build/reference/section-specify-section-attributes.md).

*FUNC-Name*\
Especifica la función que se va a llamar en lugar de `atexit` cuando termine el programa. Esta función auxiliar también llama a [AtExit](../c-runtime-library/reference/atexit.md) con un puntero al destructor para el objeto global. Si especifica un identificador de función en la instrucción pragma con el formato,

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

se llamará a su función en lugar de a `atexit` de la biblioteca en tiempo de ejecución de C. Permite crear una lista de los destructores a los que llamar cuando esté listo para destruir los objetos.

Si necesita diferir la inicialización (por ejemplo, en una DLL), puede elegir especificar el nombre de sección explícitamente. A continuación, el código debe llamar a los constructores para cada objeto estático.

No se incluyen comillas alrededor del identificador del sustituto de `atexit`.

Los objetos se seguirán colocando en las secciones definidas por `XXX_seg` otras directivas pragma.

El tiempo de ejecución de C no inicializa automáticamente los objetos que se declaran en el módulo. El código tiene que realizar la inicialización.

De forma predeterminada, las secciones `init_seg` son de solo lectura. Si el nombre de sección `.CRT`es, el compilador cambia silenciosamente el atributo a solo lectura, aunque esté marcado como de lectura y escritura.

No se puede especificar **init_seg** más de una vez en una unidad de traducción.

Incluso si el objeto no tiene un constructor definido por el usuario, uno definido explícitamente en el código, el compilador puede generar uno automáticamente. Por ejemplo, puede crear uno para enlazar punteros de tabla v. Cuando sea necesario, el código llama al constructor generado por el compilador.

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
