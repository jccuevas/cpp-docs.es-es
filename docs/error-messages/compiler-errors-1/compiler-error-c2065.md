---
title: Error del compilador C2065
ms.date: 09/01/2017
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: ae7f582de5d6c45df34c42164756356a9c794d31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482527"
---
# <a name="compiler-error-c2065"></a>Error del compilador C2065

> '*identificador*': identificador no declarado

El compilador no encuentra la declaración de un identificador. Hay varias causas posibles para este error. Las causas más comunes de C2065 son que aún no se ha declarado el identificador, el identificador está mal escrito, el encabezado donde se declara el identificador no se incluye en el archivo o el identificador no tiene un calificador de ámbito, por ejemplo, `cout` en lugar de `std::cout`. Para obtener más información sobre las declaraciones de C++, vea [declaraciones y definiciones (C++)](../../cpp/declarations-and-definitions-cpp.md).

Estos son algunos problemas comunes y soluciones con mayor detalle.

## <a name="the-identifier-is-undeclared"></a>El identificador se ha declarado

Si el identificador es una variable o un nombre de función, debe declarar antes de poder usarlo. Una declaración de función también debe incluir los tipos de sus parámetros antes de que se puede usar la función. Si la variable se declara mediante `auto`, el compilador debe ser capaz de deducir el tipo de su inicializador.

Si el identificador es un miembro de una clase o struct o declarados en un espacio de nombres, debe calificarse por el nombre de clase o struct, o el nombre del espacio de nombres, cuando se utiliza fuera del ámbito de espacio de nombres, clase o struct. Como alternativa, se debe poner el espacio de nombres en el ámbito una `using` la directiva como `using namespace std;`, o se debe poner el nombre de miembro en el ámbito una `using` declaración, como `using std::string;`. En caso contrario, el nombre no completo se considera un identificador no declarado en el ámbito actual.

Si el identificador es la etiqueta para un tipo definido por el usuario, por ejemplo, un `class` o `struct`, el tipo de la etiqueta se debe declarar antes de poder usarlo. Por ejemplo, la declaración `struct SomeStruct { /*...*/ };` debe existir antes de que se puede declarar una variable `SomeStruct myStruct;` en el código.

Si el identificador es un alias de tipo, el tipo debe declararse mediante un `using` declaración o `typedef` antes de poder usarlo. Por ejemplo, se debe declarar `using my_flags = std::ios_base::fmtflags;` antes de poder usar `my_flags` como un alias de tipo para `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Ejemplo: identificador de mal escrita

Este error suele ocurre cuando el nombre del identificador está mal escrito o el identificador usa las letras mayúsculas y minúsculas incorrectas. El nombre de la declaración debe coincidir exactamente con el nombre que use.

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

Este error puede producirse si el identificador no es el ámbito adecuado. Si ve C2065 cuando usas `cout`, esta es la causa. Cuando los operadores y funciones de la biblioteca estándar de C++ no están completamente calificados por espacio de nombres o que no haya llevado la `std` espacio de nombres en el ámbito actual mediante el uso de un `using` la directiva, el compilador no los encuentra. Para corregir este problema, debe totalmente calificar los nombres de identificador, o especifique el espacio de nombres con el `using` directiva.

En este ejemplo se produce un error al compilarse porque `cout` y `endl` se definen en el `std` espacio de nombres:

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

Los identificadores que se declaran dentro de `class`, `struct`, o `enum class` tipos también deben calificarse con el nombre de su ámbito de inclusión al usarlos fuera de ese ámbito.

## <a name="example-precompiled-header-isnt-first"></a>Ejemplo: encabezado precompilado no está primero

Este error puede producirse si coloca las directivas de preprocesador, como #include, #define, o #pragma, antes de la #include de un archivo de encabezado precompilado. Si el archivo de origen usa un archivo de encabezado precompilado (es decir, si se ha compilado mediante el uso de la **/Yu** opción del compilador), a continuación, se omiten todas las directivas de preprocesador antes del archivo de encabezado precompilado.

En este ejemplo se produce un error al compilarse porque `cout` y `endl` se definen en el \<iostream > encabezado, que se pasa por alto porque está incluido antes de que el archivo de encabezado precompilado. Para compilar este ejemplo, crear los tres archivos, compilar stdafx.cpp y, luego, compilar C2065_pch.cpp.

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
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

Para corregir este problema, agregue el #include de \<iostream > en el archivo de encabezado precompilado o mueva después del archivo de encabezado precompilado se incluye en el archivo de origen.

## <a name="example-missing-header-file"></a>Ejemplo: falta el archivo de encabezado

No se ha incluido el archivo de encabezado que declara el identificador. Asegúrese de que el archivo que contiene la declaración del identificador se incluye en cada archivo de origen que lo utiliza.

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

Otra posible causa es que si utiliza una lista de inicializadores sin incluir el \<initializer_list > encabezado.

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

Es posible que vea este error en los archivos de código fuente de aplicación de escritorio de Windows si define `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, o `WIN32_EXTRA_LEAN`. Estas macros de preprocesador excluirán algunos archivos de encabezado de windows.h y afxv\_w32.h para acelerar la compila. Busque en windows.h y afxv_w32.h una descripción actualizada de lo que se excluye.

## <a name="example-missing-closing-quote"></a>Ejemplo: falta la comilla de cierre

Este error puede producirse si faltan comillas de cierre después de una constante de cadena. Se trata de una manera fácil confundir el compilador. Tenga en cuenta que la comilla de cierre que falta puede estar varias líneas antes de la ubicación del error notificado.

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>Ejemplo: usar iterador fuera de ámbito del bucle for

Este error puede producirse si declara una variable de iterador en un `for` bucle y, a continuación, intente usar esa variable fuera del ámbito de la `for` bucle. El compilador permite la [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador de forma predeterminada. Consulte [Debug Iterator Support](../../standard-library/debug-iterator-support.md) para obtener más información.

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

## <a name="example-preprocessor-removed-declaration"></a>Ejemplo: declaración preprocesador quitado

Este error puede producirse si se hace referencia a una función o variable que está en código compilado condicionalmente que no se compila para la configuración actual. Esto también puede ocurrir si se llama a una función en un archivo de encabezado que no se admite actualmente en el entorno de compilación. Si ciertas variables o funciones solo están disponibles cuando se define una macro de preprocesador concreta, asegúrese de que solo se puede compilar el código que llama a estas funciones cuando se define la misma macro de preprocesador. Este problema es fácil de detectar en el IDE, ya que la declaración de la función está atenuada si las macros de preprocesador necesarias no están definidas para la configuración de compilación actual.

Este es un ejemplo de código que funciona cuando se compila en modo de depuración, pero no de venta directa:

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

## <a name="example-ccli-type-deduction-failure"></a>Ejemplo: C + + / error de deducción de tipo CLI

Este error puede producirse cuando se llama a una función genérica, si no se puede deducir el argumento de tipo previsto desde los parámetros utilizados. Para obtener más información, consulte [funciones genéricas (C++ / c++ / CLI)](../../windows/generic-functions-cpp-cli.md).

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

## <a name="example-ccli-attribute-parameters"></a>Ejemplo: C + + / parámetros de atributo de la CLI

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: comprobación de parámetros de atributos de Visual C++.

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
