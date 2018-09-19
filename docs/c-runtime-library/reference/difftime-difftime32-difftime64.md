---
title: difftime, _difftime32, _difftime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _difftime32
- difftime
- _difftime64
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
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
dev_langs:
- C++
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a972a8f7ee2cc5e97c22afeaa21f86e4b4d6d509
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398726"
---
# <a name="difftime-difftime32-difftime64"></a>difftime, _difftime32, _difftime64

Busca la diferencia entre dos horas.

## <a name="syntax"></a>Sintaxis

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>Parámetros

*TimeEnd*<br/>
Hora de finalización.

*TimeStart*<br/>
Hora de inicio.

## <a name="return-value"></a>Valor devuelto

**difftime** devuelve el tiempo transcurrido en segundos, de *timeStart* a *timeEnd*. El valor devuelto es un número de punto flotante de precisión doble. Puede que el valor devuelto sea 0, que indica un error.

## <a name="remarks"></a>Comentarios

El **difftime** función calcula la diferencia entre los dos valores de tiempo proporcionado *timeStart* y *timeEnd*.

El valor de tiempo proporcionado debe caber dentro del intervalo de **time_t**. **time_t** es un valor de 64 bits. Por consiguiente, el final del intervalo se ha ampliado de las 23:59:59 horas del 18 de enero de 2038, UTC a las 23:59:59 horas del 31 de diciembre de 3000. El intervalo más bajo de **time_t** sigue siendo la medianoche del 1 de enero de 1970.

**difftime** es una función insertada que se evalúa como una **_difftime32** o **_difftime64** dependiendo de si **_USE_32BIT_TIME_T** está definido. Es posible usar _difftime32 y _difftime64 directamente para forzar el uso de un tamaño concreto del tipo de tiempo.

Estas funciones validan sus parámetros. Si alguno de los parámetros es cero o negativo, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven 0 y establezca **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**difftime**|\<time.h>|
|**_difftime32**|\<time.h>|
|**_difftime64**|\<time.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}

```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038Multiplying 2 floating point numbers 100 million times...Program takes      3 seconds.Multiplying 2 floating point numbers 500 million times...

Program takes      5 seconds.
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
