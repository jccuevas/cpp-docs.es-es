---
title: Definiciones de argumentos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d30dd0c58cd4967065ee3e3c3c4df9538ea194a0
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2018
---
# <a name="argument-definitions"></a>Definiciones de argumentos
Los argumentos del prototipo  
  
```  
  
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);  
```  
  
 proporcionan una manera cómoda de analizar los argumentos en la línea de comandos y, opcionalmente, acceder a las variables de entorno. Las definiciones de los argumentos son las siguientes:  
  
 `argc`  
 Un entero que contiene el número de argumentos que aparecen detrás de `argv`. El parámetro `argc` es siempre mayor o igual que 1.  
  
 `argv`  
 Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa. Por convención, `argv` **[0]** es el comando con el que se invoca el programa, `argv` **[1]** es el primer argumento de línea de comandos y así sucesivamente, hasta que `argv`  **[**`argc`**]**, que es siempre **NULL**. Vea [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de línea de comandos.  
  
 El primer argumento de línea de comandos es siempre `argv` **[1]** y la última de ellas es `argv` **[** `argc` - 1**]**.  
  
> [!NOTE]
>  Por convención, `argv`**[0]** es el comando con el que se invoca el programa.  Sin embargo, es posible generar un proceso mediante [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) y si usa los argumentos primeros y segundo (`lpApplicationName` y `lpCommandLine`), `argv` **[0]** no puede ser el nombre del archivo ejecutable; usar [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) para recuperar el nombre del archivo ejecutable y la ruta de acceso completa.  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 `envp`  
 La matriz `envp`, que es una extensión común en muchos sistemas UNIX, se utiliza en Microsoft C++. Es una matriz de cadenas que representan las variables establecidas en el entorno de usuario. Esta matriz termina con un **NULL** entrada. Se puede declarar como una matriz de punteros a **char (char** \*envp []**)** o como un puntero para punteros a **char (char** \* \* envp**)**. Si el programa utiliza **wmain** en lugar de **principal**, use la `wchar_t` tipo de datos en lugar de `char`. El bloque de entorno pasa a **principal** y **wmain** es una copia "inmovilizada" del entorno actual. Si posteriormente cambia el entorno a través de una llamada a **putenv** o `_wputenv`, el entorno actual (devuelto por `getenv` / `_wgetenv` y `_environ` /  `_wenviron` variable) se cambio, pero el bloque al que apunta envp no cambiará. Vea [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de entorno. Este argumento es compatible con ANSI en C, pero no en C++.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `argc`, `argv`, y `envp` argumentos **principal**:  
  
```  
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