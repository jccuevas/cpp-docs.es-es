---
title: init_seg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8ec7a8d184ac8b62f6f75946d243873e0800072
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808815"
---
# <a name="initseg"></a>init_seg

**Específicos de C++**

Especifica una palabra clave o una sección de código que afecta al orden en que se ejecuta el código de inicio.

## <a name="syntax"></a>Sintaxis

```
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )
```

## <a name="remarks"></a>Comentarios

El significado de los términos *segmento* y *sección* son intercambiables en este tema.

Dado que la inicialización de objetos estáticos globales puede implicar la ejecución de código, debe especificar una palabra clave que defina cuándo deben crearse los objetos. Es especialmente importante usar el **init_seg** pragma en bibliotecas de vínculos dinámicos (DLL) o bibliotecas que requieran inicialización.

Las opciones para la **init_seg** pragma son:

*compilador*<br/>
Reservada para la inicialización de la biblioteca en tiempo de ejecución de C de Microsoft. Los objetos de este grupo se construyen en primer lugar.

*lib*<br/>
Disponible para las inicializaciones de los proveedores de bibliotecas de clases de terceros. Los objetos de este grupo se construyen después de los marcados como *compilador* pero antes de los demás.

*Usuario*<br/>
Disponible para cualquier usuario. Los objetos de este grupo se construyen en último lugar.

*nombre de sección* permite la especificación explícita de la sección de inicialización. Los objetos de la especificada por el usuario *nombre de sección* no se construyen implícitamente; sin embargo, sus direcciones se colocan en la sección designada por *nombre de sección*.

El nombre de sección que asigne contendrá punteros a funciones del asistente que construirán los objetos globales declarados en ese módulo después de la instrucción pragma.

Para obtener una lista de los nombres no debe utilizar cuando cree una sección, vea [/SECTION](../build/reference/section-specify-section-attributes.md).

*nombre de Func* especifica una función que se llamará en lugar de `atexit` cuando el programa se cierra. Esta función auxiliar también llama a [atexit](../c-runtime-library/reference/atexit.md) con un puntero al destructor del objeto global. Si especifica un identificador de función en la instrucción pragma con el formato,

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

se llamará a su función en lugar de a `atexit` de la biblioteca en tiempo de ejecución de C. Esto permite crear una lista de los destructores que deberá llamar cuando esté preparado para destruir los objetos.

Si necesita diferir la inicialización (por ejemplo, en una DLL), puede elegir especificar el nombre de sección explícitamente. En tal caso, deberá llamar a los constructores de cada objeto estático.

No se incluyen comillas alrededor del identificador del sustituto de `atexit`.

Sus objetos se incluirán igualmente en las secciones definidas por las otras instrucciones pragma XXX_seg.

El motor de tiempo de ejecución de C no inicializará automáticamente los objetos que se declaren en el módulo. Tendrá que inicializarlos usted mismo.

De forma predeterminada, las secciones `init_seg` son de solo lectura. Si el nombre de sección es .CRT, el compilador cambiará silenciosamente el atributo a de solo lectura, aunque esté marcado como de lectura o escritura.

No puede especificar **init_seg** más de una vez en una unidad de traducción.

Aunque el objeto no tenga un constructor definido por el usuario, un constructor no definido explícitamente en el código, el compilador puede generar uno (por ejemplo, para enlazar punteros de tabla v). Por consiguiente, el código tendrá que llamar al constructor generado por el compilador.

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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)