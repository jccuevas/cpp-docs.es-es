---
title: "difftime, _difftime32, _difftime64 | Microsoft Docs"
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
  - "_difftime32"
  - "difftime"
  - "_difftime64"
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
  - "_difftime64"
  - "difftime"
  - "difftime64"
  - "_difftime32"
  - "difftime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_difftime32 (función)"
  - "difftime (función)"
  - "hora, buscar la diferencia"
  - "difftime64 (función)"
  - "_difftime64 (función)"
  - "difftime32 (función)"
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# difftime, _difftime32, _difftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca la diferencia entre dos veces.  
  
## Sintaxis  
  
```  
double difftime(   
   time_t timer1,  
   time_t timer0   
);  
double _difftime32(   
   __time32_t timer1,  
   __time32_t timer0   
);  
double _difftime64(   
   __time64_t timer1,  
   __time64_t timer0   
);  
```  
  
#### Parámetros  
 `timer1`  
 Hora de finalización.  
  
 `timer0`  
 Hora de inicio.  
  
## Valor devuelto  
 `difftime` Devuelve el tiempo transcurrido en segundos, de `timer0` a `timer1`. El valor devuelto es un número de punto flotante de precisión doble. El valor devuelto puede ser 0, que indica un error.  
  
## Comentarios  
 El `difftime` función calcula la diferencia entre los dos valores de tiempo proporcionada `timer0` y `timer1`.  
  
 El valor de tiempo proporcionado debe caber dentro del intervalo de `time_t`.`time_t` es un valor de 64 bits. Por lo tanto, el final del intervalo se ha ampliado de 23:59:59 UTC del 18 de enero de 2038, a 23:59:59 del 31 de diciembre de 3000. El intervalo inferior de `time_t` sigue siendo la medianoche del 1 de enero de 1970.  
  
 `difftime` es una función insertada que se evalúa como uno `_difftime32` o `_difftime64` dependiendo de si `_USE_32BIT_TIME_T` se define. \_difftime32 y \_difftime64 pueden utilizarse directamente para forzar el uso de un determinado tamaño del tipo de tiempo.  
  
 Estas funciones validan sus parámetros. Si bien de los parámetros es cero o negativo, parámetros no válidos se invoca el controlador, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven 0 y establezca `errno` a `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`difftime`|\<time.h\>|  
|`_difftime32`|\<time.h\>|  
|`_difftime64`|\<time.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
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
Uso de punto flotante aleatorio números 1.04749e 038 2.01482e 038 1.72737e + + 038Multiplying 2 de punto flotante números 100 millones de veces... Programa tarda 3 segundos. Multiplicar 2 flotante elija números 500 millones de veces... Programa tarda 5 segundos.  
```  
  
## Equivalente en .NET Framework  
 [System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)