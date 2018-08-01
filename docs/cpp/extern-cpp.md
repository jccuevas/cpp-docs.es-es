---
title: extern (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
- extern_CPP
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 133cbb01ba54ccc8bc0ce0c31b5d7b4436c2488d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403055"
---
# <a name="extern-c"></a>extern (C++)

El **extern** palabra clave se aplica a una declaración de variable, función o plantilla global para especificar que el nombre de eso tiene *vinculación externa*. Para obtener información general sobre la vinculación y por qué no se recomienda el uso de variables globales, consulte [programa y vinculación](program-and-linkage-cpp.md).

El **extern** palabra clave tiene cuatro significados según el contexto:

1. en una declaración de variable global de no constantes, **extern** especifica que la variable o función se define en otra unidad de traducción. El **extern** deben aplicarse en todos los archivos, excepto en el que se define la variable.
1. en una declaración de variable const, especifica que la variable tiene vinculación externa. El **extern** deben aplicarse a todas las declaraciones en todos los archivos. (Las variables constantes globales tienen vinculación interna de forma predeterminada).
1. **extern "C"** especifica que la función se define en otra parte y usa la convención de llamada del lenguaje C. Modificador extern "C" también se puede aplicar a varias declaraciones de función en un bloque.
1. en una declaración de plantilla, especifica que la plantilla se ya se ha creado una instancia en otro lugar. Se trata de una optimización que le indica al compilador que puede volver a usar la creación de otra instancias en lugar de crear uno nuevo en la ubicación actual. Para obtener más información acerca de este uso de **extern**, consulte [plantillas](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>vinculación de extern para variables globales no constante

Cuando ve el vinculador **extern** antes de una declaración de variable global, busca la definición en otra unidad de traducción. Las declaraciones de variables no constante en el ámbito global son externas de forma predeterminada; solo se aplican **extern** a las declaraciones que no proporcionan la definición.

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

## <a name="extern-linkage-for-const-globals"></a>vinculación de extern para const globals

Un **const** variable global tiene vinculación interna de forma predeterminada. Si desea que la variable a tener vinculación externa, se aplican los **extern** palabra clave para la definición, así como para todas las demás declaraciones en otros archivos:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>vinculación de extern constexpr

En Visual Studio 2017 versión 15.3 y versiones anterior, el compilador siempre proporcionaba una vinculación interna de variable de constexpr, aunque la variable se marcase como extern. En la versión 15.5 de Visual Studio 2017, un nuevo conmutador de compilador ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) permite un comportamiento correcto que cumple con los estándares. Este acabará convirtiéndose en el conmutador predeterminado.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Si un archivo de encabezado contiene un constexpr variable extern declarado, debe estar marcada **__declspec (selectany)** con el fin de tener correctamente sus declaraciones duplicadas combinadas:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>las declaraciones de función extern "C" y "C++" extern

 En C++, cuando se usa con una cadena, **extern** especifica que se están usando las convenciones de vinculación de otro idioma para los declaradores. Las funciones y datos de C solo están accesibles si se declaran previamente con vinculación de C. Sin embargo, se deben definir en una unidad de traducción compilada por separado.

 Microsoft C++ admite las cadenas **"C"** y **"C++"** en el *literal de cadena* campo. Todo el estándar incluyen el uso de archivos el **extern** sintaxis de "C" para permitir que las funciones de biblioteca en tiempo de ejecución para usarse en programas de C++.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo declarar los nombres que tienen vinculación C:

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
 [Palabras clave](../cpp/keywords-cpp.md)  
 [Programa y vinculación](program-and-linkage-cpp.md)  
 [extern especificador de clase de almacenamiento en C](../c-language/extern-storage-class-specifier.md)  
 [Comportamiento de los identificadores de C](../c-language/behavior-of-identifiers.md)  
 [Vinculación de C](../c-language/linkage.md)