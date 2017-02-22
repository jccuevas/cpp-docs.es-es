---
title: "_getch, _getwch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getch"
  - "_getwch"
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
  - "getwch"
  - "_getch"
  - "_getwch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getch (función)"
  - "_getwch (función)"
  - "caracteres, obtener de consola"
  - "consola, leer"
  - "getch (función)"
  - "getwch (función)"
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _getch, _getwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un carácter de la consola sin repetición.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## Valor devuelto  
 Devuelve el carácter leído.  No se devuelve ningún error.  
  
## Comentarios  
 Las funciones `_getch` y`_getwch` leen un solo carácter de la consola sin repetición del carácter.  Ninguna de estas funciones se puede usar para leer CTRL\+C.  Al leer una tecla de función o de dirección, se debe llamar dos veces a cada función: la primera llamada devuelve 0 o 0xE0, y la segunda devuelve el código de tecla real.  
  
 Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos.  Para las versiones que no son de bloqueo, vea [\_getch\_nolock, \_getwch\_nolock](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getch`|\<conio.h\>|  
|`_getwch`|\<conio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getch.c  
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
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
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