---
title: Definiciones de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 044c5df5ae0a51912893ccf306a5c93afceb7ab3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407593"
---
# <a name="argument-definitions"></a>Definiciones de argumentos
Los argumentos del prototipo  
  
```cpp 
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);  
```  
  
 proporcionan una manera cómoda de analizar los argumentos en la línea de comandos y, opcionalmente, acceder a las variables de entorno. Las definiciones de los argumentos son las siguientes:  
  
 *argc*  
 Un entero que contiene el recuento de argumentos que siguen en *argv*. El *argc* parámetro siempre es mayor o igual que 1.  
  
 *argv*  
 Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa. Por convención, `argv` **[0]** es el comando con el que se invoca el programa, `argv` **[1]** es el primer argumento de línea de comandos y así sucesivamente, hasta `argv`  **[**`argc`**]**, que siempre es NULL. Consulte [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de línea de comandos.  
  
 El primer argumento de línea de comandos siempre es `argv` **[1]** y el último es `argv` **[** `argc` - 1 **]**.  
  
> [!NOTE]
>  Por convención, `argv`**[0]** es el comando con el que se invoca el programa.  Sin embargo, es posible generar un proceso usando [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) y si usa los argumentos primeros y segundo (*lpApplicationName* y *lpCommandLine*), `argv` **[0]** no puede ser el archivo ejecutable nombre; use [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) para recuperar el nombre del archivo ejecutable y su ruta de acceso completa.  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 *envp*  
 El *envp* matriz, que es una extensión común en muchos sistemas UNIX, se usa en Microsoft C++. Es una matriz de cadenas que representan las variables establecidas en el entorno de usuario. Esta matriz finaliza mediante una entrada NULL. Se puede declarar como una matriz de punteros a **char (char** \*envp []**)** o como un puntero para punteros a **char (char** \* \* envp **)**. Si el programa utiliza `wmain` en lugar de `main`, utilice el `wchar_t` en lugar del tipo de datos **char**. El bloque de entorno pasa a `main` y `wmain` es una copia "inmovilizada" del entorno actual. Si se cambia posteriormente el entorno a través de una llamada a `putenv` o `_wputenv`, el entorno actual (devuelto por `getenv` / `_wgetenv` y `_environ` /  `_wenviron` variable) le cambiar, pero el bloque apunta envp no cambiará. Consulte [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de entorno. Este argumento es compatible con ANSI en C, pero no en C++.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar el *argc*, *argv*, y *envp* argumentos `main`:  
  
```cpp 
// argument_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
int main( int argc, char *argv[], char *envp[] ) {  
    int iNumberLines = 0;    // Default is no line numbers.  
  
    // If /n is passed to the .exe, display numbered listing  
    // of environment variables.  
  
    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )  
         iNumberLines = 1;  
  
    // Walk through list of strings until a NULL is encountered.  
    for( int i = 0; envp[i] != NULL; ++i ) {  
        if( iNumberLines )  
            cout << i << ": " << envp[i] << "\n";  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 
  [main: Inicio de programa](../cpp/main-program-startup.md)