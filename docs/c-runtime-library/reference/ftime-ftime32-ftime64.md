---
title: "_ftime, _ftime32, _ftime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftime64"
  - "_ftime"
  - "_ftime32"
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
  - "_ftime32"
  - "_ftime"
  - "_ftime64"
  - "ftime64"
  - "ftime"
  - "ftime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ftime64 (función)"
  - "_ftime64 (función)"
  - "hora actual"
  - "_ftime (función)"
  - "ftime (función)"
  - "_ftime32 (función)"
  - "ftime32 (función)"
  - "hora, obtener actual"
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _ftime, _ftime32, _ftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la hora actual.  Hay disponibles versiones más seguras de estas funciones; vea [\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md).  
  
## Sintaxis  
  
```  
void _ftime(   
   struct _timeb *timeptr   
);  
void _ftime32(   
   struct __timeb32 *timeptr   
);  
void _ftime64(   
   struct __timeb64 *timeptr   
);  
```  
  
#### Parámetros  
 `timeptr`  
 Puntero a `_timeb`,a`__timeb32` o estructura de `__timeb64` .  
  
## Comentarios  
 La función de `_ftime` obtiene la hora local y la almacena en la estructura designada por a *`timeptr`.* `_timeb`, `__timeb32`,ylas estructuras de`__timeb64` se definen en SYS\\Timeb.h.  Contienen cuatro campos, que se enumeran en la tabla siguiente.  
  
 `dstflag`  
 Distinto de cero si el horario de verano está actualmente en vigor para la zona horaria local. \(Vea [\_tzset](../../c-runtime-library/reference/tzset.md) para obtener una explicación de cómo se determina el horario de verano.\)  
  
 `millitm`  
 Fracción segundo en milisegundos.  
  
 `time`  
 Tiempo en segundos desde la medianoche \(00:00: 00\), el 1 de enero de 1970, hora universal coordinada \(UTC\).  
  
 `timezone`  
 Diferencia en minutos, desplazándose hacia el oeste, entre la hora utc y la hora local.  El valor de `timezone` se establece el valor de la variable global `_timezone` \(vea `_tzset`\).  
  
 `_ftime64`, que utiliza la estructura de `__timeb64` , permite que las fechas de creación de archivos se expresadas hacia arriba con 23:59: 59, el 31 de diciembre, 3000, hora UTC; mientras que `_ftime32` sólo representa las fechas con 03:14: 7 de enero de 19, 2038, La hora UTC.  La medianoche, el 1 de enero de 1970, es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 `_ftime` es equivalente a `_ftime64` y `_timeb` contiene una hora 64 bits.  Esto es así a menos que se defina `_USE_32BIT_TIME_T` , en cuyo caso el comportamiento antiguo está vigente; `_ftime` utiliza un período de 32 bits y `_timeb` contiene un plazo de 32 bits.  
  
 `_ftime` valida sus parámetros.  Si se pasa un puntero NULL como `timeptr`, la función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` a `EINVAL`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_ftime`|\<sistema\/types.h y\> sistema \<\/timeb.h\>|  
|`_ftime32`|\<sistema\/types.h y\> sistema \<\/timeb.h\>|  
|`_ftime64`|\<sistema\/types.h y\> sistema \<\/timeb.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_ftime.c  
// compile with: /W3  
// This program uses _ftime to obtain the current  
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
  
   _ftime( &timebuffer ); // C4996  
   // Note: _ftime is deprecated; consider using _ftime_s instead  
  
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
  
  **Segundos desde medianoche, el 1 de enero de 1970 \(hora UTC\): 1051553334**  
**Milisegundos: 230**  
**Minutos entre la hora utc y la hora local: 480**  
**Indicador del horario de verano \(1 significa que el tiempo de Daylight está vigente\): 1**  
**El tiempo es monday el 28 de abril de 11: 08:54.230 2003**   
## Equivalente en .NET Framework  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)