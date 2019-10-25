---
title: Error del compilador C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 40d1d0744588c4b7911e84f5e57a6b40372b48cf
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630132"
---
# <a name="compiler-error-c2065"></a>Error del compilador C2065

> '*Identifier*': identificador no declarado

El compilador no puede encontrar la declaración de un identificador. Hay muchas causas posibles de este error. Las causas más comunes de C2065 son que el identificador no se ha declarado, el identificador está mal escrito, el encabezado en el que se declara el identificador no está incluido en el archivo o el identificador no tiene un calificador de ámbito, por ejemplo, `cout` en lugar de `std::cout`. Para obtener más información sobre las declaraciones C++en, vea [declaraciones y definiciones (C++)](../../cpp/declarations-and-definitions-cpp.md).

Estos son algunos problemas y soluciones comunes con mayor detalle.

## <a name="the-identifier-is-undeclared"></a>El identificador no está declarado

Si el identificador es una variable o un nombre de función, debe declararlo para poder utilizarlo. Una declaración de función también debe incluir los tipos de sus parámetros antes de que se pueda usar la función. Si la variable se declara mediante `auto`, el compilador debe ser capaz de deducir el tipo de su inicializador.

Si el identificador es un miembro de una clase o struct, o se declara en un espacio de nombres, se debe calificar con el nombre de clase o struct, o el nombre de espacio de nombres, cuando se usa fuera del ámbito de estructura, clase o espacio de nombres. Como alternativa, el espacio de nombres debe incluirse en el `using` ámbito mediante una `using namespace std;`Directiva como, o bien el nombre del miembro debe incluirse `using` en el ámbito mediante `using std::string;`una declaración, como. De lo contrario, el nombre no completo se considera un identificador no declarado en el ámbito actual.

Si el identificador es la etiqueta de un tipo definido por el usuario, por ejemplo, `class` o `struct`, se debe declarar el tipo de la etiqueta antes de que se pueda usar. Por ejemplo, la declaración `struct SomeStruct { /*...*/ };` debe existir antes de poder declarar una variable `SomeStruct myStruct;` en el código.

Si el identificador es un alias de tipo, el tipo se debe declarar mediante una `using` declaración o `typedef` antes de que se pueda usar. Por ejemplo, debe declarar `using my_flags = std::ios_base::fmtflags;` antes de que pueda usar `my_flags` como un alias de tipo para. `std::ios_base::fmtflags`

## <a name="example-misspelled-identifier"></a>Ejemplo: identificador mal escrito

Este error suele producirse cuando el nombre del identificador está mal escrito o el identificador usa letras mayúsculas y minúsculas equivocadas. El nombre de la declaración debe coincidir exactamente con el nombre que use.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>Ejemplo: usar un identificador sin ámbito

Este error puede producirse si el identificador no tiene el ámbito adecuado. Si ve C2065 cuando usa `cout`, esta es la causa. Cuando C++ las funciones y los operadores de la biblioteca estándar no están totalmente calificados por el espacio de `std` nombres o no se ha puesto el espacio `using` de nombres en el ámbito actual mediante una directiva, el compilador no puede encontrarlos. Para corregir este problema, debe calificar totalmente los nombres de los identificadores o especificar el espacio de nombres `using` con la Directiva.

No se puede compilar `cout` este `endl` ejemplo porque y se `std` definen en el espacio de nombres:

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

Los identificadores que se declaran `struct`dentro de `enum class` `class`los tipos, o también se deben calificar con el nombre de su ámbito de inclusión cuando se usan fuera de ese ámbito.

## <a name="example-precompiled-header-isnt-first"></a>Ejemplo: el encabezado precompilado no es primero

Este error puede producirse si se colocan directivas de preprocesador, como #include, #define o #pragma, antes del #include de un archivo de encabezado precompilado. Si el archivo de código fuente utiliza un archivo de encabezado precompilado (es decir, si se compila con la opción del compilador **/Yu** ), se omiten todas las directivas de preprocesador antes del archivo de encabezado precompilado.

No se puede compilar `cout` este `endl` ejemplo porque y se \<definen en el encabezado de > de iostream, que se omite porque se incluye antes del archivo de encabezado precompilado. Para compilar este ejemplo, cree los tres archivos, compile stdafx. cpp y, a continuación, compile C2065_pch. cpp.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

Para corregir este problema, agregue el #include de \<iostream > al archivo de encabezado precompilado o muévalo después de incluir el archivo de encabezado precompilado en el archivo de código fuente.

## <a name="example-missing-header-file"></a>Ejemplo: falta el archivo de encabezado

No incluyó el archivo de encabezado que declara el identificador. Asegúrese de que el archivo que contiene la declaración para el identificador está incluido en cada archivo de código fuente que lo usa.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

Otra posible causa es el uso de una lista de inicializadores sin incluir \<el encabezado > initializer_list.

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

Puede ver este error en los archivos de origen de la aplicación de escritorio `VC_EXTRALEAN`de `WIN32_LEAN_AND_MEAN`Windows si `WIN32_EXTRA_LEAN`define, o. Estas macros de preprocesador excluyen algunos archivos de encabezado de Windows. h\_y afxv W32. h para acelerar las compilaciones. Busque en Windows. h y afxv_w32. h una descripción actualizada de lo que se excluye.

## <a name="example-missing-closing-quote"></a>Ejemplo: falta la comilla de cierre

Este error puede producirse si falta una comilla de cierre después de una constante de cadena. Se trata de una manera sencilla de confundir el compilador. Tenga en cuenta que las comillas de cierre que faltan pueden tener varias líneas antes de la ubicación del error.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>Ejemplo: usar un iterador fuera del ámbito del bucle

Este error puede producirse si se declara una variable de iterador en un `for` bucle e intenta usar esa variable `for` de iterador fuera del ámbito del bucle. El compilador habilita de forma predeterminada la opción del compilador [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . Para obtener más información, consulte [compatibilidad con iteradores](../../standard-library/debug-iterator-support.md) de depuración.

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>Ejemplo: la declaración del preprocesador quitado

Este error puede producirse si se hace referencia a una función o variable que está en código compilado condicionalmente que no se compila para la configuración actual. Esto también puede ocurrir si se llama a una función en un archivo de encabezado que no se admite actualmente en el entorno de compilación. Si algunas variables o funciones solo están disponibles cuando se define una macro de preprocesador determinada, asegúrese de que el código que llama a esas funciones solo se puede compilar cuando se define la misma macro de preprocesador. Este problema es fácil de detectar en el IDE, ya que la declaración de la función está atenuada si no se han definido las macros de preprocesador necesarias para la configuración de compilación actual.

Este es un ejemplo de código que funciona al compilar en depurar, pero no a minorista:

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>Ejemplo: C++/CLI error de deducción de tipo

Este error puede producirse cuando se llama a una función genérica, si el argumento de tipo previsto no se puede deducir a partir de los parámetros utilizados. Para obtener más información, consulte [funciones genéricasC++(/CLI)](../../extensions/generic-functions-cpp-cli.md).

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>Ejemplo: C++/CLI parámetros de atributo

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: comprobación de parámetros para los C++ atributos visuales.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
