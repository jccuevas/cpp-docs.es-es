---
title: "Definiciones de argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argc (argumento)"
  - "argumentos [C++], para función main"
  - "argv (argumento)"
  - "envp (argumento)"
  - "main (función), argumentos"
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Definiciones de argumentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los argumentos del prototipo  
  
```  
  
int main( int argc[ , char *argv[ ] [, char *envp[ ] ] ] ); int wmain( int argc[ , wchar_t *argv[ ] [, wchar_t *envp[ ] ] ] );  
```  
  
 proporcionan una manera cómoda de analizar los argumentos en la línea de comandos y, opcionalmente, acceder a las variables de entorno.  Las definiciones de los argumentos son las siguientes:  
  
 `argc`  
 Un entero que contiene el número de argumentos que aparecen detrás de `argv`.  El parámetro `argc` es siempre mayor o igual que 1.  
  
 `argv`  
 Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa.  Por convención, `argv`**\[0\]** es el comando con el que se invoca el programa, `argv`**\[1\]** es el primer argumento de la línea de comandos, etc., hasta `argv`**\[**`argc`**\]**, que siempre es **NULL**.  Vea [Personalizar el procesamiento de la línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de la línea de comandos.  
  
 El primer argumento de la línea de comandos siempre es `argv`**\[1\]** y el último es `argv`**\[**`argc` – 1**\]**.  
  
> [!NOTE]
>  Por convención, `argv`**\[0\]** es el comando con el que se invoca el programa.  Sin embargo, es posible generar un proceso mediante [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) y, si usa el primer y el segundo argumento \(`lpApplicationName` y `lpCommandLine`\), `argv`**\[0\]** puede que no sea el nombre ejecutable; use [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) para recuperar el nombre ejecutable y la ruta de acceso completa.  
  
## Específicos de Microsoft  
 `envp`  
 La matriz `envp`, que es una extensión común en muchos sistemas UNIX, se utiliza en Microsoft C\+\+.  Es una matriz de cadenas que representan las variables establecidas en el entorno de usuario.  Esta matriz termina con una entrada **NULL**.  Puede declararse como una matriz de punteros a **char \(char** \*envp\[ \]**\)** o como un puntero a punteros a **char \(char** \*\*envp**\)**.  Si su programa usa **wmain** en lugar de **main**, utilice el tipo de datos `wchar_t` en lugar de `char`.  El bloque de entorno que se pasa a **main** y a **wmain** es una copia "inmóvil" del entorno actual.  Si posteriormente cambia el entorno mediante una llamada a **putenv** o `_wputenv`, el entorno actual \(devuelto por `getenv`\/`_wgetenv` y las variables `_environ`\/ `_wenviron`\) cambiará, pero el bloque al que apunta envp no cambiará.  Vea [Personalizar el procesamiento de la línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento del entorno.  Este argumento es compatible con ANSI en C, pero no en C\+\+.  
  
## FIN de Específicos de Microsoft  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar los argumentos `argc`, `argv` y `envp` de **main**:  
  
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
  
## Vea también  
 [main: inicio de programa](../cpp/main-program-startup.md)