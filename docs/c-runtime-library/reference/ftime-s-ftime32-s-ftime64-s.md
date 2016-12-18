---
title: "_ftime_s, _ftime32_s, _ftime64_s | Microsoft Docs"
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
  - "_ftime_s"
  - "_ftime64_s"
  - "_ftime32_s"
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
  - "_ftime_s"
  - "_ftime64_s"
  - "ftime_s"
  - "_ftime32_s"
  - "ftime32_s"
  - "ftime64_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ftime32_s (función)"
  - "ftime_s (función)"
  - "_ftime64_s (función)"
  - "hora actual"
  - "ftime64_s (función)"
  - "hora, obtener actual"
  - "_ftime_s (función)"
  - "_ftime32_s (función)"
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ftime_s, _ftime32_s, _ftime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la hora actual. Estas son versiones de [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### Parámetros  
 `timeptr`  
 Puntero a un `_timeb,``__timeb32`, o `__timeb64` estructura.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si `timeptr` es `NULL`, el valor devuelto es `EINVAL`.  
  
## Comentarios  
 El `_ftime_s` función obtiene la hora local actual y lo almacena en la estructura que señala `timeptr`*.* El `_timeb,``__timeb32`,y`__timeb64` estructuras se definen en SYS\\Timeb.h. Contienen cuatro campos, que se enumeran en la tabla siguiente.  
  
 `dstflag`  
 Distinto de cero si el horario de verano está en vigor para la zona horaria local. \(Consulte [\_tzset](../../c-runtime-library/reference/tzset.md) para obtener una explicación de cómo se determina el horario de verano.\)  
  
 `millitm`  
 Fracción de segundo en milisegundos.  
  
 `time`  
 Tiempo en segundos transcurridos desde la medianoche \(00: 00:00\) del 1 de enero de 1970, hora universal coordinada \(UTC\).  
  
 `timezone`  
 Diferencia en minutos, westward, mover entre la hora UTC y la hora local. El valor de `timezone` se establece el valor de la variable global `_timezone` \(consulte `_tzset`\).  
  
 `_ftime64_s`, que utiliza el `__timeb64` estructura, permite expresar de hasta 23:59:59, hasta el 31 de diciembre de 3000, UTC; las fechas de creación del archivo, mientras que `_ftime32_s` solo representa fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC. La noche del 1 de enero de 1970, es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 `_ftime_s` es equivalente a `_ftime64_s` y `_timeb` contiene una hora de 64 bits. Esto es cierto a menos que \_`USE_32BIT_TIME_T` definido, en cuyo caso el comportamiento anterior está en vigor; \_`ftime_s` usa un tiempo de 32 bits y `_timeb` contiene una hora de 32 bits.  
  
 `_ftime_s` valida sus parámetros. Si pasa un puntero nulo como `timeptr`, la función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` a `EINVAL`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_ftime_s`|\< sys\/types.h \> y \< sys\/timeb.h \>|  
|`_ftime32_s`|\< sys\/types.h \> y \< sys\/timeb.h \>|  
|`_ftime64_s`|\< sys\/types.h \> y \< sys\/timeb.h \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime64_s( &timebuffer );  
  
    time1 = timebuffer.time;  
    millitm1 = timebuffer.millitm;  
    timezone1 = timebuffer.timezone;  
    dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
```Output  
Segundos transcurridos desde la medianoche del 1 de enero de 1970 (UTC): 1051553334 milisegundos: 230 minutos entre la hora UTC y la hora local: (1 significa horario de verano está en vigor) de la marca de horario de 480 verano: 1 la hora es 11:08:54.230 lunes 28 de abril de 2003  
```  
  
## Equivalente en .NET Framework  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)