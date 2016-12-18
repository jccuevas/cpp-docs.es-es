---
title: "localtime, _localtime32, _localtime64 | Microsoft Docs"
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
  - "_localtime64"
  - "_localtime32"
  - "localtime"
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
  - "localtime64"
  - "_localtime64"
  - "localtime32"
  - "localtime"
  - "_localtime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "localtime32 (función)"
  - "_localtime32 (función)"
  - "_localtime64 (función)"
  - "localtime64 (función)"
  - "localtime (función)"
  - "hora, convertir valores"
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localtime, _localtime32, _localtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convertir un valor de hora y corregir de la zona horaria local. Existen versiones más seguras de estas funciones; consulte [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).  
  
## Sintaxis  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### Parámetros  
 `timer`  
 Puntero a la hora almacenada.  
  
## Valor devuelto  
 Devolver un puntero al resultado de la estructura, o `NULL` Si la fecha que se pasa a la función es:  
  
-   Antes de la medianoche del 1 de enero de 1970.  
  
-   Después de 03:14:07 del 19 de enero de 2038, hora UTC \(mediante `_time32` y `time32_t`\).  
  
-   Después de 23:59:59 del 31 de diciembre de 3000, UTC \(mediante `_time64` y `__time64_t`\).  
  
 `_localtime64`, que utiliza el `__time64_t` estructura, permite expresar 23:59:59 del 31 de diciembre de 3000, hora universal coordinada \(UTC\), fechas, mientras que `_localtime32` representa fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
 `localtime` es una función insertada que se evalúa como `_localtime64`, y `time_t` es equivalente a `__time64_t`. Si necesita que el compilador interprete `time_t`como lo 32 bits anterior `time_t`, puede definir `_USE_32BIT_TIME_T`. Hacer esto hará que `localtime` se evalúe como `_localtime32`. Esto no se recomienda porque puede producir un error de la aplicación después del 18 de enero de 2038, y no se permite en plataformas de 64 bits.  
  
 Los campos de tipo de estructura [tm](../../c-runtime-library/standard-types.md) almacenar los valores siguientes, cada uno de los cuales es una `int`:  
  
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
  
## Comentarios  
 El `localtime` función convierte una hora que se almacenan como un [time\_t](../../c-runtime-library/standard-types.md) valor y almacena el resultado en una estructura de tipo `tm`. El `long` valor `timer` representa los segundos transcurridos desde la medianoche \(00: 00:00\) del 1 de enero de 1970, hora UTC. Este valor suele obtenerse a partir del `time` \(función\).  
  
 Las versiones de 32 bits y 64 bits de `gmtime`, `mktime`, `mkgmtime`, y `localtime` utilizan un único `tm` estructura por subproceso para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.  
  
 `localtime` corrige la zona horaria local si el usuario establece primero la variable de entorno global `TZ`. Cuando `TZ` se establece, otras tres variables de entorno \(`_timezone`, `_daylight`, y `_tzname`\) se establece también automáticamente. Si el `TZ` no se establece la variable, `localtime` intenta utilizar la información de zona horaria especificada en la aplicación de fecha y hora en el Panel de Control. Si no se puede obtener esta información, se usa PST8PDT, lo que significa la zona horaria del Pacífico, de forma predeterminada. Consulte [\_tzset](../../c-runtime-library/reference/tzset.md) para obtener una descripción de estas variables.`TZ` es una extensión de Microsoft y no forma parte de la definición del estándar ANSI de `localtime`.  
  
> [!NOTE]
>  El entorno de destino debería intentar determinar si el horario de verano está en vigor.  
  
 Estas funciones validan sus parámetros. Si `timer` es un puntero nulo, o si el valor del temporizador es negativo, estas funciones invocan un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven `NULL` y establecen `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`localtime`|\<time.h\>|  
|`_localtime32`|\<time.h\>|  
|`_localtime64`|\<time.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
Martes 12 de febrero 10:05:58 A.M.  
```  
  
## Equivalente en .NET Framework  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)