---
title: "clock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clock"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "clock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "calcular el tiempo de procesador usado"
  - "clock (función)"
  - "tiempo de procesador usado"
  - "tiempo de procesador usado, calcular"
  - "hora, calcular para procesador"
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# clock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el tiempo de reloj usado por el proceso de llamada.  
  
## Sintaxis  
  
```  
clock_t clock( void );  
```  
  
## Valor devuelto  
 Tiempo de reloj transcurrido desde el inicio del proceso \(tiempo transcurrido en segundos `CLOCKS_PER_SEC`\).  Si el tiempo transcurrido no está disponible, la función devuelve \-1, convertido como `clock_t`.  
  
## Comentarios  
 La función `clock` indica el tiempo de reloj que el proceso de llamada ha usado.  Tenga en cuenta que esto no es estrictamente compatible con ISO C99, que especifica el tiempo de CPU neto como el valor devuelto.  Para obtener el tiempo de CPU, use la función de Win32 [GetProcessTimes](http://msdn.microsoft.com/library/windows/desktop/ms683223).  
  
 Un paso del temporizador equivale aproximadamente a 1\/`CLOCKS_PER_SEC` segundos.  Con el tiempo suficiente, el valor devuelto por `clock` puede superar el valor positivo máximo de `clock_t` y pasa a ser negativo, o bien superar el valor absoluto máximo y continuar.  Prescinda de este valor de tiempo total transcurrido cuando los procesos se hayan ejecutado durante más de 214.748 segundos o 59 horas aproximadamente.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`clock`|\<time.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_clock.c  
// This example prompts for how long  
// the program is to run and then continuously  
// displays the elapsed time for that period.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
void sleep( clock_t wait );  
  
int main( void )  
{  
   long    i = 6000000L;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   printf( "Time to do %ld empty loops is ", i );  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "%2.1f seconds\n", duration );  
}  
  
// Pauses for a specified number of milliseconds.  
void sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
```  
  
  **Delay for three seconds**  
**Done\!  Time to do 6000000 empty loops is 0.1 seconds**    
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [difftime, \_difftime32, \_difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)