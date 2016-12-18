---
title: "_fputc_nolock, _fputwc_nolock | Microsoft Docs"
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
  - "_fputwc_nolock"
  - "_fputc_nolock"
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
  - "_fputc_nolock"
  - "fputwc_nolock"
  - "fputc_nolock"
  - "fputtc_nolock"
  - "_fputwc_nolock"
  - "_fputtc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fputc_nolock (función)"
  - "_fputtc_nolock (función)"
  - "_fputwc_nolock (función)"
  - "fputc_nolock (función)"
  - "fputtc_nolock (función)"
  - "fputwc_nolock (función)"
  - "secuencias, escribir caracteres en"
ms.assetid: c63eb3ad-58fa-46d0-9249-9c25f815eab9
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fputc_nolock, _fputwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en un flujo sin bloquear el subproceso.  
  
## Sintaxis  
  
```  
int _fputc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _fputwc_nolock(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el carácter escrito.  Para obtener información sobre errores, vea [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md).  
  
## Comentarios  
 `_fputc_nolock` y `_fputwc_nolock` son exactamente iguales que `fputc` y `fputwc`, respectivamente, salvo que no están protegidas contra interferencias de otros subprocesos.  Pueden ser más rápidas porque no incurren en la sobrecarga de bloquear otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
 Las dos funciones se comportan igual si el flujo se abre en modo ANSI.  `_fputc_nolock` no admite actualmente la salida a un flujo UNICODE.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fputtc_nolock`|`_fputc_nolock`|`_fputc_nolock`|`_fputwc_nolock`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fputc_nolock`|\<stdio.h\>|  
|`_fputwc_nolock`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_fputc_nolock.c  
// This program uses _fputc_nolock  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of _fputc_nolock!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && _fputc_nolock( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
  **This is a test of \_fputc\_nolock\!\!**   
## Equivalente en .NET Framework  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)