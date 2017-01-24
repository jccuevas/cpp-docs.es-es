---
title: "_putchar_nolock, _putwchar_nolock | Microsoft Docs"
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
  - "_putchar_nolock"
  - "_putwchar_nolock"
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
apitype: "DLLExport"
f1_keywords: 
  - "putwchar_nolock"
  - "_puttchar_nolock"
  - "_putchar_nolock"
  - "_putwchar_nolock"
  - "putchar_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putchar_nolock (función)"
  - "_puttchar_nolock (función)"
  - "_putwchar_nolock (función)"
  - "caracteres, escribir"
  - "putchar_nolock (función)"
  - "puttchar_nolock (función)"
  - "putwchar_nolock (función)"
  - "salida estándar, escribir"
ms.assetid: 9ac68092-bfc3-4352-b486-c3e780220575
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putchar_nolock, _putwchar_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en **stdout** sin bloquear el subproceso.  
  
## Sintaxis  
  
```  
  
      int _putchar_nolock(  
   int c   
);  
wint_t _putwchar_nolock(  
   wchar_t c   
);  
  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
## Valor devuelto  
 Vea **putchar, putwchar**.  
  
## Comentarios  
 **putchar\_nolock** y `_putwchar_nolock` son exactamente iguales que las versiones sin el sufijo **\_nolock**, salvo que no están protegidas contra interferencias de otros subprocesos.  Pueden ser más rápidas porque no incurren en la sobrecarga de bloquear otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_puttchar_nolock`|`_putchar_nolock`|`_putchar_nolock`|`_putwchar_nolock`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_putchar_nolock`|\<stdio.h\>|  
|`_putwchar_nolock`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_putchar_nolock.c  
/* This program uses putchar to write buffer  
 * to stdout. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = _putchar_nolock( *p );  
}  
```  
  
## Resultados  
  
```  
This is the line of output  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)