---
title: "_kbhit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_kbhit"
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
  - "_kbhit"
  - "kbhit"
  - "conio/_kbhit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_kbhit (función)"
  - "consola"
  - "consola, comprobar"
  - "kbhit (función)"
  - "entrada mediante teclado"
  - "teclados, comprobar entrada"
  - "teclados, entrada mediante teclado"
  - "datos proporcionados por el usuario, comprobar si hay teclado"
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _kbhit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si hay acciones del teclado en la consola.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
int _kbhit( void );  
```  
  
## Valor devuelto  
 `_kbhit` devuelve un valor distinto de cero si se ha presionado una tecla.  De lo contrario, devuelve 0.  
  
## Comentarios  
 La función `_kbhit` comprueba en la consola si se ha presionado una tecla recientemente.  Si la función devuelve un valor distinto de cero, hay una pulsación de tecla esperando en el búfer.  A continuación, el programa puede llamar a `_getch` o `_getche` para obtener la pulsación de tecla.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_kbhit`|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_kbhit.c  
// compile with: /c  
/* This program loops until the user  
 * presses a key. If _kbhit returns nonzero, a  
 * keystroke is waiting in the buffer. The program  
 * can call _getch or _getche to get the keystroke.  
 */  
  
#include <conio.h>  
#include <stdio.h>  
  
int main( void )  
{  
   /* Display message until key is pressed. */  
   while( !_kbhit() )  
      _cputs( "Hit me!! " );  
  
   /* Use _getch to throw key away. */  
   printf( "\nKey struck was '%c'\n", _getch() );  
}  
```  
  
## Resultados del ejemplo  
  
```  
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!  
Key struck was 'q'   
```  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)