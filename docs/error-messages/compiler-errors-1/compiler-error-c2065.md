---
title: Error del compilador C2065 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 5a3a0d4389a958f421f23a4dc96a395eaf3e22ab
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2065"></a>Error del compilador C2065
'identificador': identificador no declarado  
  
El compilador no puede encontrar la declaración de un identificador. Si el identificador es una variable, debe especificar el tipo de la variable en una declaración antes de poder utilizarlo. Si el identificador es un nombre de función, los parámetros que utiliza la función deben especificarse en una declaración para poder usar la función. Si el identificador es la etiqueta para un tipo definido por el usuario, por ejemplo, un `class` o `struct`, el tipo de la etiqueta se debe declarar antes de poder utilizarlo. Si el identificador es un alias de tipo, el tipo debe declararse mediante un `using` declaración o `typedef` para poder usar el tipo.  
  
Hay varias causas posibles para este error. Estos son algunos de los problemas más comunes:
  
## <a name="example-misspelled-identifier"></a>Ejemplo: identificador de mal escrita  
  
Este error suele producirse cuando el nombre del identificador está mal escrito, o el identificador usa las letras mayúsculas y minúsculas incorrectas. El nombre de la declaración debe coincidir exactamente con el nombre que utiliza.  
  
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
  
## <a name="example-missing-header-file"></a>Ejemplo: falta el archivo de encabezado  
  
No se ha incluido el archivo de encabezado que declara el identificador. Asegúrese de que el archivo que contiene la declaración del identificador se incluye en cada archivo de código fuente que lo utilice.  
  
```cpp  
// C2065_header.cpp  
// compile with: cl /EHsc C2065_spell.cpp 

//#include <stdio.h> 
int main() { 
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier 
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined  
} 
```  
  
Puede ver este error en archivos de código fuente de aplicación de escritorio de Windows si define `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, o `WIN32_EXTRA_LEAN`. Estas macros de preprocesador excluirán algunos archivos de encabezado de windows.h y afxv\_w32.h para acelerar compila. Busque en windows.h y afxv_w32.h una descripción actualizada de lo que se excluye.  
  
## <a name="eample-missing-closing-quote"></a>Eample: falta la comilla de cierre  
  
Este error puede producirse si falta una comilla de cierre después de una constante de cadena. Se trata de una manera fácil confundir el compilador. 
  
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
  
Este error puede producirse si se declara una variable de iteración en una `for` bucle y, a continuación, pruebe a utilizar esa variable fuera del ámbito de la `for` bucle. Permite que el compilador la [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador de forma predeterminada. Vea [Debug Iterator Support](../../standard-library/debug-iterator-support.md) para obtener más información.  
  
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
  
## <a name="example-preprocessor-removed-declaration"></a>Ejemplo: declaración quitado preprocesador  
  
Este error puede producirse si se hace referencia a una función o variable que está en código compilado condicionalmente que no se compila para la configuración actual. Esto también puede ocurrir si se llama a una función en un archivo de encabezado que no se admite actualmente en el entorno de compilación. Si ciertas variables o funciones solo están disponibles cuando se define una macro de preprocesador concreta, asegúrese de que solo se puede compilar el código que llama a estas funciones cuando se define la macro de preprocesador mismo. Este problema es fácil detectar en el IDE, dado que la declaración de la función está atenuada si las macros de preprocesador necesarias no estén definidas para la configuración de compilación actual.  
  
Este es un ejemplo de código que funciona cuando se compila en versiones de depuración, pero no por menor:  
  
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
  
## <a name="example-use-an-unscoped-identifier"></a>Ejemplo: usar un identificador sin ámbito  
  
Este error puede producirse si el identificador no tiene un ámbito correctamente. Por ejemplo, cuando los operadores y funciones de la biblioteca estándar de C++ no están completamente calificados por el espacio de nombres o no haya llevado la `std` espacio de nombres en el ámbito actual mediante el uso de un `using` la directiva, el compilador no puede encontrarlos. Para corregir este problema, debe totalmente calificar los nombres de identificador, o especifique el espacio de nombres con el `using` directiva.  
  
En este ejemplo se produce un error de compilación porque `cout` y `endl` se definen en el `std` espacio de nombres:  
  
```cpp  
// C2065_scope.cpp  
// compile with: cl /EHsc C2065_scope.cpp 
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier 
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead  
    std::cout << "Hello" << std::endl;  
}
```  
  
Los identificadores que se declaran dentro de `class`, `struct`, o `enum class` tipos, también se deben calificar el nombre del ámbito de inclusión.
  
## <a name="example-ccli-type-deduction-failure"></a>Ejemplo: C++ / error de deducción de tipo CLI  
  
Este error puede producirse cuando se llama a una función genérica, si no se puede deducir el argumento de tipo previsto desde los parámetros usados. Para obtener más información, consulte [funciones genéricas (C++ / CLI)](../../windows/generic-functions-cpp-cli.md).  
  
```cpp  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## <a name="example-ccli-attribute-parameters"></a>Ejemplo: C++ / parámetros de atributo CLI  
  
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

