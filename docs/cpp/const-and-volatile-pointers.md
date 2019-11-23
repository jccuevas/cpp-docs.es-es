---
title: punteros const y volatile
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c0aafde9070275abcb270710e2d4a7a8d9806267
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246626"
---
# <a name="const-and-volatile-pointers"></a>punteros const y volatile

Las palabras clave [const](const-cpp.md) y [volatile](volatile-cpp.md) cambian el modo en que se tratan los punteros. La palabra clave **const** especifica que el puntero no se puede modificar después de la inicialización; el puntero está protegido contra la modificación después.

La palabra clave **volatile** especifica que el valor asociado al nombre que se indica a continuación puede ser modificado por acciones distintas de las de la aplicación de usuario. Por lo tanto, la palabra clave **volatile** es útil para declarar objetos en la memoria compartida a los que pueden tener acceso varios procesos o áreas de datos globales que se usan para la comunicación con rutinas de servicio de interrupción.

Cuando un nombre se declara como **volatile**, el compilador recarga el valor de la memoria cada vez que el programa obtiene acceso a él. Esto reduce considerablemente las posibles optimizaciones. Sin embargo, cuando el estado de un objeto puede cambiar de forma inesperada, es la única forma garantizar un rendimiento predecible del programa.

Para declarar el objeto al que apunta el puntero como **const** o **volatile**, use una declaración con el formato:

```cpp
const char *cpch;
volatile char *vpch;
```

Para declarar el valor del puntero, es decir, la dirección real almacenada en el puntero (como **const** o **volatile**), utilice una declaración con el formato:

```cpp
char * const pchc;
char * volatile pchv;
```

El C++ lenguaje impide las asignaciones que permitan la modificación de un objeto o puntero declarado como **const**. Estas asignaciones quitarían la información con la que se declaró el objeto o puntero, infringiendo así la intención de la declaración original. Considere las siguientes declaraciones:

```cpp
const char cch = 'A';
char ch = 'B';
```

Dadas las declaraciones anteriores de dos objetos (`cch`, de tipo **const char**y `ch`, de tipo **Char)** , las siguientes declaraciones o inicializaciones son válidas:

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

La declaración o inicializaciones siguientes son erróneas.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

La declaración de `pch2` declara un puntero a través del cual podría modificarse un objeto constante y, por consiguiente, no se permite. La declaración de `pch3` especifica que el puntero es constante, no el objeto; la declaración no se permite por la misma razón que la declaración de `pch2` no está permitida.

Las ocho asignaciones siguientes muestran la asignación a través de un puntero y cómo se cambia el valor del puntero para las declaraciones anteriores; por ahora, supongamos que la inicialización era correcta para las declaraciones de `pch1` a `pch8`.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

Los punteros declarados como **volatile**o como una combinación de **const** y **volatile**obedecen a las mismas reglas.

Los punteros a objetos **const** se suelen usar en declaraciones de función de la manera siguiente:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

La instrucción anterior declara una función, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), donde dos de los tres argumentos son de tipo Pointer a **Char**. Dado que los argumentos se pasan por referencia y no por valor, la función sería gratuita para modificar `strDestination` y `strSource` si `strSource` no se declararon como **const**. La declaración de `strSource` como **const** garantiza que el llamador que `strSource` no pueda cambiar la función a la que se llama.

> [!NOTE]
> Dado que hay una conversión estándar de *typename* <strong>\*</strong> a **const** *TypeName* <strong>\*</strong>, es válido pasar un argumento de tipo `char *` a [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Sin embargo, lo contrario no es cierto. no existe ninguna conversión implícita para quitar el atributo **const** de un objeto o puntero.

Un puntero **const** de un tipo determinado se puede asignar a un puntero del mismo tipo. Sin embargo, un puntero que no es **const** no se puede asignar a un puntero **const** . El código siguiente muestra las asignaciones correctas e incorrectas:

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

En el ejemplo siguiente se muestra cómo declarar un objeto como const si tiene un puntero a un puntero a un objeto.

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>Vea también

[Punteros](pointers-cpp.md)
[punteros sin formato](raw-pointers.md)