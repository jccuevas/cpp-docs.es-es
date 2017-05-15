---
title: localtime_s, _localtime32_s, _localtime64_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e068c6711630976a2d8b3baea01010bc5e34ed6e
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s
Convierte un valor de hora y lo corrige para la zona horaria local. Estas son versiones de [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `_tm`  
 Puntero a la estructura de tiempo que debe rellenarse.  
  
 `time`  
 Puntero a la hora almacenada.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, vea [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`_tm`|`time`|Valor devuelto|Valor de `_tm`|Invoca el controlador de parámetros no válidos|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|cualquiera|`EINVAL`|No modificado|Sí|  
|No `NULL` (apunta a la memoria válida)|`NULL`|`EINVAL`|Todos los campos establecidos en -1|Sí|  
|No `NULL` (apunta a la memoria válida)|menor que 0 o mayor que `_MAX__TIME64_T`|`EINVAL`|Todos los campos establecidos en -1|No|  
  
 En el caso de las dos primeras condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_localtime32_s` convierte una hora almacenada como valor [time_t](../../c-runtime-library/standard-types.md) y almacena el resultado en una estructura de tipo `tm`. El valor `long` `timer` representa los segundos transcurridos desde la medianoche (00:00:00) del 1 de enero de 1970, hora UTC. Este valor suele obtenerse a partir de la función `time`.  
  
 `_localtime32_s` corrige la zona horaria local si el usuario establece primero la variable de entorno global `TZ`. Si se establece `TZ`, también se establecen automáticamente otras tres variables de entorno (`_timezone`, `_daylight` y `_tzname`). Si no se establece la variable `TZ`, `localtime32_s` intenta usar la información de la zona horaria especificada en la aplicación de fecha y hora del Panel de Control. Si no se puede obtener esta información, se usa de forma predeterminada PST8PDT, que significa la zona horaria del Pacífico. Vea [_tzset](../../c-runtime-library/reference/tzset.md) para obtener una descripción de estas variables. `TZ` es una extensión de Microsoft y no forma parte de la definición del estándar ANSI de `localtime`.  
  
> [!NOTE]
>  El entorno de destino debería intentar determinar si el horario de verano está vigente.  
  
 `_localtime64_s`, que usa la estructura `__time64_t`, permite expresar fechas hasta las 23:59:59 del 18 de enero de 3001, hora universal coordinada (UTC), mientras que `_localtime32_s` representa fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
 `localtime_s` es una función insertada que se evalúa como `_localtime64_s` y `time_t` es equivalente a `__time64_t`. Si necesita forzar el compilador para interpretar `time_t` como el antiguo `time_t` de 32 bits, puede definir `_USE_32BIT_TIME_T`. Al hacerlo, `localtime_s` se evaluará como `_localtime32_s`. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.  
  
 Los campos del tipo de estructura [tm](../../c-runtime-library/standard-types.md) almacenan los valores siguientes, cada uno de los cuales es un `int`.  
  
 `tm_sec`  
 Segundos después del minuto (0 - 59).  
  
 `tm_min`  
 Minutos después de la hora (0 - 59).  
  
 `tm_hour`  
 Horas después de la medianoche (0 - 23).  
  
 `tm_mday`  
 Día del mes (1-31).  
  
 `tm_mon`  
 Mes (0 - 11; Enero = 0).  
  
 `tm_year`  
 Año (año actual menos 1900).  
  
 `tm_wday`  
 Día de la semana (0 - 6; El domingo = 0).  
  
 `tm_yday`  
 Día del año (0 - 365; El 1 de enero = 0).  
  
 `tm_isdst`  
 Valor positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; valor negativo si se desconoce el estado del horario de verano. Si se establece la variable de entorno `TZ`, la biblioteca en tiempo de ejecución de C usa las reglas correspondientes a los Estados Unidos para implementar el cálculo del horario de verano (DST).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`localtime_s`|\<time.h>|  
|`_localtime32_s`|\<time.h>|  
|`_localtime64_s`|\<time.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)

