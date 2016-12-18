---
title: "_fgetchar, _fgetwchar | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fgetchar"
  - "_fgetwchar"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fgetwchar"
  - "_fgettchar"
  - "_fgetchar"
  - "_fgetwchar"
  - "fgettchar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetchar (función)"
  - "_fgettchar (función)"
  - "_fgetwchar (función)"
  - "fgetchar (función)"
  - "fgettchar (función)"
  - "fgetwchar (función)"
  - "entrada estándar, leer"
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fgetchar, _fgetwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee un carácter de una cadena `stdin`.  
  
## Sintaxis  
  
```  
int _fgetchar( void );  
wint_t _fgetwchar( void );  
```  
  
## Valor devuelto  
 `_fgetchar` devuelve el carácter leído como `int`, o `EOF` para indicar un error o un final de archivo.  **\_**`fgetwchar` devuelve, en forma de [wint\_t](../../c-runtime-library/standard-types.md), el carácter ancho correspondiente al carácter leído, o devuelve `WEOF` para indicar un error o un final de archivo.  En el caso de las dos funciones, use `feof` o `ferror` diferenciar un error de una condición de fin de archivo.  
  
## Comentarios  
 Estas funciones leen un solo carácter de `stdin`.  A continuación, la función aumenta el puntero de archivo asociado \(si está definido\) para señalar al carácter siguiente.  Si el flujo está al final del archivo, se establece la marca de fin de archivo para el flujo.  
  
 `_fgetchar` es equivalente a `fgetc( stdin )`.  También equivale a `getchar`, pero implementado solo como función, y no como una función y una macro.  `_fgetwchar` es la versión con caracteres anchos de `_fgetchar`.  
  
 Estas funciones no son compatibles con el estándar ANSI.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fgettchar`|`_fgetchar`|`_fgetchar`|`_fgetwchar`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fgetchar`|\<stdio.h\>|  
|`_fgetwchar`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_fgetchar.c  
// This program uses _fgetchar to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[81];  
   int  i, ch;  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = _fgetchar();  
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetchar();  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
}  
```  
  
  **`Línea uno. Línea dos.`Línea uno.**  
**Línea dos.**   
## Equivalente en .NET Framework  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)