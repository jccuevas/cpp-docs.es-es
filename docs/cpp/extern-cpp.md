---
title: extern (C++)
description: Guía de la C++ palabra clave Language extern.
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821771"
---
# <a name="opno-locextern-c"></a>extern (C++)

La palabra clave **extern** se puede aplicar a una declaración de variable, función o plantilla global. Especifica que el símbolo tiene *vinculación externa*. Para obtener información general sobre la vinculación y el motivo por el que no se recomienda el uso de variables globales, vea [unidades de traducción y vinculación](program-and-linkage-cpp.md).

La palabra clave **extern** tiene cuatro significados según el contexto:

- En una declaración de variable global no **const** , **extern** especifica que la variable o función está definida en otra unidad de traducción. El **extern** debe aplicarse en todos los archivos excepto en el que se define la variable.

- En una declaración de variable de **const** , especifica que la variable tiene vinculación externa. El **extern** debe aplicarse a todas las declaraciones de todos los archivos. (Las variables globales **const** tienen vinculación interna de forma predeterminada).

- **extern "C"** especifica que la función se define en otra parte y usa la Convención de llamada del lenguaje C. El modificador extern "C" también se puede aplicar a varias declaraciones de función en un bloque.

- En una declaración de plantilla, **extern** especifica que ya se ha creado una instancia de la plantilla en otro lugar. **extern** le indica al compilador que puede volver a usar la otra instancia, en lugar de crear una nueva en la ubicación actual. Para obtener más información sobre este uso de **extern** , vea [creación de instancias explícitas](explicit-instantiation.md).

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>extern vinculación para globales que no son deconst

Cuando el vinculador ve **extern** antes de una declaración de variable global, busca la definición en otra unidad de traducción. Las declaraciones de variables que no son de **const** en el ámbito global son externas de forma predeterminada. Aplique solo **extern** a las declaraciones que no proporcionan la definición.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>vinculación extern para las globales de const

De forma predeterminada, una variable global **const** tiene vinculación interna. Si desea que la variable tenga vinculación externa, aplique la palabra clave **extern** a la definición y a todas las demás declaraciones de otros archivos:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>vinculación de constexpr de extern

En la versión 15,3 de Visual Studio 2017 y versiones anteriores, el compilador siempre dio una vinculación interna de **constexpr** variable, incluso cuando la variable se marcaba como **extern** . En la versión 15,5 de Visual Studio 2017 y versiones posteriores, el modificador de compilador [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) habilita el comportamiento correcto conforme a los estándares. Finalmente, la opción se convertirá en el valor predeterminado. La opción de [-permissivede/](../build/reference/permissive-standards-conformance.md) no habilita **/Zc: externConstexpr**.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene una variable declarada **extern** **constexpr** , debe marcarse como `__declspec(selectany)` para que se combinen correctamente sus declaraciones duplicadas:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern declaraciones de función "C"C++y extern ""

En C++, cuando se usa con una cadena, **extern** especifica que se usan las convenciones de vinculación de otro lenguaje para los declaradores. Solo se puede tener acceso a las funciones y los datos de c si se han declarado previamente como una vinculación de C. Sin embargo, se deben definir en una unidad de traducción compilada por separado.

Microsoft C++ admite las cadenas **"C"** y **"C++"** en el campo de *literal de cadena* . Todos los archivos de inclusión estándar utilizan la sintaxis de **extern "C"** para permitir que las funciones de la biblioteca en tiempo de C++ ejecución se utilicen en los programas.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo declarar nombres que tienen vinculación C:

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

Si una función tiene más de una especificación de vinculación, deben coincidir. Es un error declarar funciones como con C y C++ vinculación. Además, si en un programa aparecen dos declaraciones para una función (una con una especificación de vinculación y otra sin ella), la declaración con especificación de vinculación debe ser la primera. Cualquier declaración redundante de funciones que ya tengan especificación de vinculación recibe la vinculación especificada en la primera declaración. Por ejemplo:

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)\
[Unidades de traducción y vinculación](program-and-linkage-cpp.md)\
[extern especificador de clase de almacenamiento en C](../c-language/extern-storage-class-specifier.md)\
[Comportamiento de los identificadores en C](../c-language/behavior-of-identifiers.md)\
[Vinculación en C](../c-language/linkage.md)
