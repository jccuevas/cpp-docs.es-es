---
title: "_getch_nolock, _getwch_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getwch_nolock"
  - "_getch_nolock"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getch_nolock"
  - "getwch_nolock"
  - "getch_nolock"
  - "_getwch_nolock"
  - "_gettch_nolock"
  - "gettch_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getch_nolock (función)"
  - "_gettch_nolock (función)"
  - "_getwch_nolock (función)"
  - "caracteres, obtener de consola"
  - "consola, leer"
  - "getch_nolock (función)"
  - "gettch_nolock (función)"
  - "getwch_nolock (función)"
ms.assetid: 9d248546-26ca-482c-b0c6-55812a987e83
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getch_nolock, _getwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un carácter de la consola sin repetición y sin bloquear el subproceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _getch_nolock( void );  
wint_t _getwch_nolock( void );  
```  
  
## Valor devuelto  
 Devuelve el carácter leído.  No se devuelve ningún error.  
  
## Comentarios  
 `_getch_nolock` y `_getwch_nolock` son exactamente iguales que `_getch` y`_getchw`, salvo que no están protegidas contra interferencias de otros subprocesos.  Pueden ser más rápidas porque no incurren en la sobrecarga de bloquear otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_gettch_nolock`|`_getch_nolock`|`_getch_nolock`|`_getwch_nolock`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getch_nolock`|\<conio.h\>|  
|`_getwch_nolock`|\<conio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getch_nolock.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch_nolock();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch_nolock( ch );  
   _putch_nolock( '\r' );    // Carriage return  
   _putch_nolock( '\n' );    // Line feed  
}  
```  
  
  **`abcdey`Escriba 'Y' cuando termine de escribir: Y**   
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_getche, \_getwche](../../c-runtime-library/reference/getche-getwche.md)   
 [\_cgets, \_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch, \_ungetwch, \_ungetch\_nolock, \_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)