---
title: "localtime_s, _localtime32_s, _localtime64_s | Microsoft Docs"
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
  - "_localtime64_s"
  - "_localtime32_s"
  - "localtime_s"
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
  - "_localtime32_s"
  - "localtime32_s"
  - "localtime_s"
  - "localtime64_s"
  - "_localtime64_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_localtime64_s (función)"
  - "localtime32_s (función)"
  - "_localtime32_s (función)"
  - "localtime64_s (función)"
  - "hora, convertir valores"
  - "localtime_s (función)"
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localtime_s, _localtime32_s, _localtime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un valor de hora y corrige la zona horaria local. Estas son versiones de [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### Parámetros  
 `_tm`  
 Puntero a la estructura de tiempo que deben rellenarse.  
  
 `time`  
 Puntero a la hora almacenada.  
  
## Valor devuelto  
 Cero si es correcta. El valor devuelto es un código de error si se produce un error. Códigos de error se definen en Errno.h. Para obtener una lista de estos errores, vea [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### Condiciones de error  
  
|`_tm`|`time`|Valor devuelto|Valor de `_tm`|Se invoca el controlador de parámetros no válidos|  
|-----------|------------|--------------------|--------------------|-------------------------------------------------------|  
|`NULL`|any|`EINVAL`|No modificado|Sí|  
|No `NULL` \(puntos de memoria válida\)|`NULL`|`EINVAL`|Todos los campos valor \-1|Sí|  
|No `NULL` \(puntos de memoria válida\)|menor que 0 o mayor que `_MAX__TIME64_T`|`EINVAL`|Todos los campos valor \-1|No|  
  
 En el caso de las condiciones de error primeras, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## Comentarios  
 El `_localtime32_s` función convierte una hora que se almacenan como un [time\_t](../../c-runtime-library/standard-types.md) valor y almacena el resultado en una estructura de tipo `tm`. El `long` valor `timer` representa los segundos transcurridos desde la medianoche \(00: 00:00\) del 1 de enero de 1970, hora UTC. Este valor suele obtenerse a partir del `time` \(función\).  
  
 `_localtime32_s` corrige la zona horaria local si el usuario establece primero la variable de entorno global `TZ`. Cuando `TZ` se establece, otras tres variables de entorno \(`_timezone`, `_daylight`, y `_tzname`\) se establece también automáticamente. Si el `TZ` no se establece la variable, `localtime32_s` intenta utilizar la información de zona horaria especificada en la aplicación de fecha y hora en el Panel de Control. Si no se puede obtener esta información, se usa PST8PDT, lo que significa la zona horaria del Pacífico, de forma predeterminada. Consulte [\_tzset](../../c-runtime-library/reference/tzset.md) para obtener una descripción de estas variables.`TZ` es una extensión de Microsoft y no forma parte de la definición del estándar ANSI de `localtime`.  
  
> [!NOTE]
>  El entorno de destino debería intentar determinar si el horario de verano está en vigor.  
  
 `_localtime64_s`, que utiliza el `__time64_t` estructura, permite expresar 23:59:59 del 31 de diciembre de 3000, hora universal coordinada \(UTC\), fechas, mientras que `_localtime32_s` representa fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
 `localtime_s` es una función insertada que se evalúa como `_localtime64_s`, y `time_t` es equivalente a `__time64_t`. Si necesita forzar el compilador para interpretar `time_t` como el antiguo `time_t` de 32 bits, puede definir `_USE_32BIT_TIME_T`. Hacer esto hará que `localtime_s` se evalúe como `_localtime32_s`. Esto no se recomienda porque puede producir un error de la aplicación después del 18 de enero de 2038, y no se permite en plataformas de 64 bits.  
  
 Los campos de tipo de estructura [tm](../../c-runtime-library/standard-types.md) almacenar los valores siguientes, cada uno de los cuales es una `int`.  
  
 `tm_sec`  
 Segundos después del minuto \(0 – 59\).  
  
 `tm_min`  
 Minutos después de la hora \(0 – 59\).  
  
 `tm_hour`  
 Horas después de la medianoche \(0 – 23\).  
  
 `tm_mday`  
 Día del mes \(1 – 31\).  
  
 `tm_mon`  
 Mes \(0 – 11; Enero \= 0\).  
  
 `tm_year`  
 Año \(año actual menos 1900\).  
  
 `tm_wday`  
 Día de la semana \(0 – 6; Domingo \= 0\).  
  
 `tm_yday`  
 Día del año \(0 – 365; 1 de enero \= 0\).  
  
 `tm_isdst`  
 Valor positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; valor negativo si se desconoce el estado del horario de verano. Si el `TZ` se establece la variable de entorno, la biblioteca de tiempo de ejecución de C asume que las reglas adecuada a los Estados Unidos para implementar el cálculo del horario de verano \(DST\).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`localtime_s`|\<time.h\>|  
|`_localtime32_s`|\<time.h\>|  
|`_localtime64_s`|\<time.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## Resultados del ejemplo  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## Equivalente en .NET Framework  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)