---
title: extern (C++)
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301540"
---
# <a name="extern-c"></a>extern (C++)

La palabra clave **extern** se aplica a una declaración de variable, función o plantilla global para especificar que el nombre de ese elemento tiene *vinculación externa*. Para obtener información general sobre la vinculación y el motivo por el que no se recomienda el uso de variables globales, vea [unidades de traducción y vinculación](program-and-linkage-cpp.md).

La palabra clave **extern** tiene cuatro significados según el contexto:

1. en una declaración de variable global no const, **extern** especifica que la variable o función está definida en otra unidad de traducción. **Extern** debe aplicarse en todos los archivos excepto en el que se define la variable.
1. en una declaración de variable const, especifica que la variable tiene vinculación externa. **Extern** debe aplicarse a todas las declaraciones de todos los archivos. (Las variables globales const tienen vinculación interna de forma predeterminada).
1. **extern "C"** especifica que la función se define en otra parte y usa la Convención de llamada del lenguaje C. El modificador extern "C" también se puede aplicar a varias declaraciones de función en un bloque.
1. en una declaración de plantilla, especifica que ya se ha creado una instancia de la plantilla en otro lugar. Se trata de una optimización que indica al compilador que puede volver a usar la otra instancia en lugar de crear una nueva en la ubicación actual. Para obtener más información sobre este uso de **extern**, consulte [plantillas](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>vinculación externa para globales no const

Cuando el vinculador ve **extern** delante de una declaración de variable global, busca la definición en otra unidad de traducción. Las declaraciones de variables no const en el ámbito global son externas de forma predeterminada; solo se aplica **extern** a las declaraciones que no proporcionan la definición.

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

## <a name="extern-linkage-for-const-globals"></a>vinculación externa para Globals const

Una variable global **const** tiene vinculación interna de forma predeterminada. Si desea que la variable tenga vinculación externa, aplique la palabra clave **extern** a la definición, así como a todas las demás declaraciones de otros archivos:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>vinculación externa constexpr

En la versión 15,3 y anteriores de Visual Studio 2017, el compilador siempre dio una vinculación interna de variable constexpr incluso cuando la variable se marcó como extern. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) permite un comportamiento correcto que cumple con los estándares. Este acabará convirtiéndose en el conmutador predeterminado. La opción/permissive-no habilita/ZC: externConstexpr.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene una variable declarada extern constexpr, debe marcarse como **__declspec (selectany)** para tener correctamente combinadas las declaraciones duplicadas:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>declaraciones de función extern "C"C++y extern ""

En C++, cuando se usa con una cadena, **extern** especifica que se usan las convenciones de vinculación de otro idioma para los declaradores. Las funciones y datos de C solo están accesibles si se declaran previamente con vinculación de C. Sin embargo, se deben definir en una unidad de traducción compilada por separado.

Microsoft C++ admite las cadenas **"C"** y **"C++"** en el campo de *literal de cadena* . Todos los archivos de inclusión estándar utilizan la sintaxis **extern** "C" para permitir que las funciones de la biblioteca en tiempo de ejecución C++ se utilicen en los programas.

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

Si una función tiene más de una especificación de vinculación, deben coincidir; es un error declarar funciones que tengan tanto vinculación de C como de C++. Además, si en un programa aparecen dos declaraciones para una función (una con una especificación de vinculación y otra sin ella), la declaración con especificación de vinculación debe ser la primera. Cualquier declaración redundante de funciones que ya tengan especificación de vinculación recibe la vinculación especificada en la primera declaración. Por ejemplo:

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

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Unidades de traducción y vinculación](program-and-linkage-cpp.md)<br/>
[extern (especificador de clase de almacenamiento) en C](../c-language/extern-storage-class-specifier.md)<br/>
[Comportamiento de los identificadores en C](../c-language/behavior-of-identifiers.md)<br/>
[Vinculación en C](../c-language/linkage.md)