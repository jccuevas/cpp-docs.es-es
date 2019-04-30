---
title: Punteros const y volatile
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c869adbbdc8a5a17d315e64e5ac15545e0c46e26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399127"
---
# <a name="const-and-volatile-pointers"></a>Punteros const y volatile

El [const](../cpp/const-cpp.md) y [volátil](../cpp/volatile-cpp.md) palabras clave cambiar cómo se tratan los punteros. El **const** palabra clave especifica que el puntero no se puede modificar después de la inicialización; el puntero está protegido contra modificaciones a partir de entonces.

El **volátil** palabra clave especifica que se puede modificar el valor asociado con el nombre que sigue las acciones que no estén en la aplicación de usuario. Por lo tanto, el **volátil** palabra clave es útil para declarar objetos en la memoria compartida que se puede acceder mediante varios procesos o áreas de datos globales usadas para la comunicación con rutinas de interrupción de servicio.

Cuando se declara un nombre como **volátil**, el compilador vuelve a cargar el valor de la memoria cada vez que se accede mediante el programa. Esto reduce considerablemente las posibles optimizaciones. Sin embargo, cuando el estado de un objeto puede cambiar de forma inesperada, es la única forma garantizar un rendimiento predecible del programa.

Para declarar el objeto al que señala el puntero como **const** o **volátil**, utilice una declaración con el formato:

```cpp
const char *cpch;
volatile char *vpch;
```

Para declarar el valor del puntero, es decir, la dirección real almacenada en el puntero, como **const** o **volátil**, utilice una declaración de la forma:

```cpp
char * const pchc;
char * volatile pchv;
```

El lenguaje C++ evita asignaciones que pudieran permitir la modificación de un objeto o un puntero declarado como **const**. Estas asignaciones quitarían la información con la que se declaró el objeto o puntero, infringiendo así la intención de la declaración original. Considere las siguientes declaraciones:

```cpp
const char cch = 'A';
char ch = 'B';
```

Dadas las declaraciones anteriores de dos objetos (`cch`, del tipo **const char**, y `ch`, del tipo **char)**, la declaración o inicializaciones siguientes son válidas:

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

La declaración de `pch2` declara un puntero a través del cual podría modificarse un objeto constante y, por consiguiente, no se permite. La declaración de `pch3` especifica que el puntero es constante, no el objeto; la declaración no está permitida por la misma razón el `pch2` no se permite la declaración.

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

Los punteros declarados como **volátil**, o como una mezcla de **const** y **volátil**, siguen las mismas reglas.

Punteros a **const** objetos a menudo se usan en las declaraciones de función como sigue:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

La instrucción anterior declara una función, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), donde dos de los tres argumentos son de tipo puntero a **char**. Dado que los argumentos se pasan por referencia y no por valor, la función sería modificar libremente `strDestination` y `strSource` si `strSource` no se declaró como **const**. La declaración de `strSource` como **const** garantiza al llamador que `strSource` no se puede cambiar la función llamada.

> [!NOTE]
> Dado que hay una conversión estándar de *typename* <strong>\*</strong> a **const** *typename* <strong>\*</strong>, es legal para pasar un argumento de tipo `char *` a [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Sin embargo, no es true; de lo contrario no existe ninguna conversión implícita para quitar el **const** atributo de un objeto o puntero.

Un **const** puntero de un tipo determinado se puede asignar a un puntero del mismo tipo. Sin embargo, un puntero que no es **const** no se puede asignar un **const** puntero. El código siguiente muestra las asignaciones correctas e incorrectas:

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

[Punteros](../cpp/pointers-cpp.md)