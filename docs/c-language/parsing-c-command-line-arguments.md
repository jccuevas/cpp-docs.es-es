---
title: "Analizar los argumentos de la línea de comandos de C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3db47ca48e52babc03923dfba7b1dcb8173cc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analizar los argumentos de la línea de comandos de C
**Específicos de Microsoft**  
  
 El código de inicio de Microsoft C utiliza las reglas siguientes al interpretar los argumentos proporcionados en la línea de comandos del sistema operativo:  
  
-   Los argumentos van delimitados por espacio en blanco, que puede ser un carácter de espacio o una tabulación.  
  
-   Una cadena entre comillas dobles se interpreta como un solo argumento, sin importar el espacio en blanco que contenga. Se puede incrustar una cadena entre comillas dentro de un argumento. Observe que el carácter de intercalación (**^**) no se reconoce como carácter de escape ni como delimitador.  
  
-   Un signo de comillas dobles precedido por una barra diagonal inversa, **\\"**, se interpreta como signo de comillas dobles literal (**"**).  
  
-   Las barras diagonales inversas se interpretan literalmente, a menos que precedan inmediatamente a unas comillas.  
  
-   Si un número par de barras diagonales inversas va seguido de un signo de comillas dobles, se coloca una barra diagonal inversa (**\\**) en la matriz `argv` por cada par de barras diagonales inversas (**\\\\**) y el signo de comillas dobles (**"**) se interpreta como delimitador de cadenas.  
  
-   Si un número impar de barras diagonales inversas va seguido de un signo de comillas dobles, se coloca una barra diagonal inversa (**\\**) en la matriz `argv` por cada par de barras diagonales inversas (**\\\\**) y el signo de comillas dobles se interpreta como carácter de escape debido a la barra diagonal inversa restante, lo que hace que se ponga un signo de comillas dobles literal (**"**) en `argv`.  
  
 En esta lista se muestran las reglas anteriores y el resultado interpretado que se pasa a `argv` para varios ejemplos de argumentos de la línea de comandos. La salida que se muestra en las columnas segunda, tercera y cuarta proviene del programa ARGS.C que sigue a la lista.  
  
|Entrada de la línea de comandos|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"a b c" d e`|`a b c`|`d`|`e`|  
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|  
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
```  
// Parsing_C_Commandline_args.c  
// ARGS.C illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
//  
  
#include <stdio.h>  
  
int main( int argc, // Number of strings in array argv  
 char *argv[],      // Array of command-line argument strings  
 char **envp )      // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf_s( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf_s( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.  
    printf_s( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf_s( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
## <a name="comments"></a>Comentarios  
 Un ejemplo de la salida de este programa es:  
  
```  
Command-line arguments:  
  argv[0]   C:\MSC\TEST.EXE  
  
Environment variables:  
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE  
  
  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;  
  PROMPT=[$p]   
  TEMP=c:\tmp  
  TMP=c:\tmp  
  EDITORS=c:\binr  
  WINDIR=c:\nt        
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)