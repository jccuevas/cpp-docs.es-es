---
title: clock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- clock
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
dev_langs:
- C++
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3a226377499df1747a022325b762b3cdfdd35ea6
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="clock"></a>clock
Calcula el tiempo de reloj usado por el proceso de llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
clock_t clock( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
El tiempo transcurrido desde la inicialización de CRT al principio del proceso, medido en unidades por segundo `CLOCKS_PER_SEC`. Si el tiempo transcurrido no está disponible o ha superado el tiempo máximo positivo que puede registrarse como un tipo `clock_t`, la función devuelve el valor `(clock_t)(-1)`.   
  
## <a name="remarks"></a>Comentarios  
La función `clock` indica el tiempo de reloj que ha transcurrido desde la inicialización de CRT durante el inicio del proceso. Tenga en cuenta que esta función no se ajusta estrictamente a ISO C, que especifica el tiempo de CPU neto como el valor devuelto. Para obtener tiempos de CPU, use la función [GetProcessTimes](https://msdn.microsoft.com/library/windows/desktop/ms683223) de Win32. Para determinar el tiempo transcurrido en segundos, divida el valor devuelto por la función `clock` mediante la macro `CLOCKS_PER_SEC`.  
  
Con el tiempo suficiente, el valor devuelto por `clock` puede superar el valor positivo máximo de `clock_t`. Cuando el proceso se ha ejecutado durante más tiempo, el valor devuelto por `clock` siempre es `(clock_t)(-1)`, tal y como especifica el estándar ISO C99 (7.23.2.1) y el estándar ISO C11 (7.27.2.1). Microsoft implementa `clock_t` como `long`, un entero de 32 bits con signo, y la macro `CLOCKS_PER_SEC` se define como 1000. Esto proporciona un máximo valor devuelto de la función `clock` de 2.147.483,647 segundos o aproximadamente 24,8 días. No se base en el valor devuelto por `clock` en los procesos que se han ejecutado durante más tiempo. Puede usar la función `time` de 64 bits o la función [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) de Windows para registrar los tiempos transcurridos de proceso de muchos años.  

## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`clock`|\<time.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_clock.c  
// This sample uses clock() to 'sleep' for three 
// seconds, then determines how long it takes  
// to execute an empty loop 600000000 times.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
// Pauses for a specified number of milliseconds.  
void do_sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
  
const long num_loops = 600000000L;

int main( void )  
{  
   long    i = num_loops;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "Time to do %ld empty loops is ", num_loops );  
   printf( "%2.3f seconds\n", duration );  
}  
```  
  
```Output  
Delay for three seconds  
Done!  
Time to do 600000000 empty loops is 1.354 seconds  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [difftime, _difftime32, _difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)
