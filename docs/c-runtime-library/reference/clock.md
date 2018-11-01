---
title: clock
ms.date: 11/04/2016
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
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 4b58b33b533250447cf964134de9869bddee4498
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492658"
---
# <a name="clock"></a>clock

Calcula el tiempo de reloj usado por el proceso de llamada.

## <a name="syntax"></a>Sintaxis

```C
clock_t clock( void );
```

## <a name="return-value"></a>Valor devuelto

El tiempo transcurrido desde la inicialización de CRT al principio del proceso, medido en **CLOCKS_PER_SEC** unidades por segundo. Si el tiempo transcurrido no está disponible o ha superado el tiempo máximo positivo que puede registrarse como un **clock_t** tipo, la función devuelve el valor `(clock_t)(-1)`.

## <a name="remarks"></a>Comentarios

El **reloj** función indica cuánto tiempo de reloj transcurrido desde que la inicialización de CRT durante el inicio del proceso. Tenga en cuenta que esta función no se ajusta estrictamente a ISO C, que especifica el tiempo de CPU neto como el valor devuelto. Para obtener tiempos de CPU, use la función [GetProcessTimes](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) de Win32. Para determinar el tiempo transcurrido en segundos, divida el valor devuelto por la **reloj** función mediante la macro **CLOCKS_PER_SEC**.

Con el tiempo suficiente, el valor devuelto por **reloj** puede superar el valor positivo máximo de **clock_t**. Cuando el proceso ha ejecutado más tiempo, el valor devuelto por **reloj** siempre `(clock_t)(-1)`, tal y como especifica el estándar ISO C99 (7.23.2.1) y el estándar ISO C11 (7.27.2.1). Microsoft implementa **clock_t** como un **largo**, un entero de 32 bits con signo y el **CLOCKS_PER_SEC** macro se define como 1000. Esto proporciona un máximo **reloj** función de valor devuelto de 2.147.483,647 segundos o aproximadamente 24,8 días. No confíe en el valor devuelto por **reloj** en procesos que se han ejecutado durante más tiempo que esta cantidad de tiempo. Puede usar el modo de 64 bits [tiempo](time-time32-time64.md) función o el Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) función a los tiempos transcurridos de proceso de registro de muchos años.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**clock**|\<time.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
