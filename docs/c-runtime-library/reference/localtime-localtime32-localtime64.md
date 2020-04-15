---
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 21496b71c354c7bed7b87526dc40bc9b24865da2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342134"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Convierte un valor de hora y lo corrige para la zona horaria local. Hay disponibles versiones más seguras de estas funciones; vea [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Sintaxis

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parámetros

*sourceTime*<br/>
Puntero a la hora almacenada.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al resultado de la estructura, o **NULL** si la fecha pasada a la función es:

- Antes de la medianoche del 1 de enero de 1970.

- Después de 03:14:07, 19 de enero de 2038, UTC (usando **_time32** y **time32_t).**

- Después de las 23:59:59, 31 de diciembre de 3000, UTC (usando **_time64** y **__time64_t**).

**_localtime64**, que utiliza la estructura **__time64_t,** permite que las fechas se expresen hasta las 23:59:59, 31 de diciembre de 3000, hora universal coordinada (UTC), mientras que **_localtime32** representa fechas hasta las 23:59:59 del 18 de enero de 2038, UTC.

**localtime** es una función en línea que se evalúa como **_localtime64**y **time_t** es equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como el **antiguo time_t**de 32 bits, puede definir **_USE_32BIT_TIME_T**. Si lo hace, la **hora local** se evaluará como **_localtime32**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

Los campos del tipo de estructura [tm](../../c-runtime-library/standard-types.md) almacenan los siguientes valores, cada uno de los cuales es un **int:**

|Campo|Descripción|
|-|-|
|**tm_sec**|Segundos tras minuto (0 - 59).|
|**tm_min**|Minutos después de la hora (0 - 59).|
|**tm_hour**|Horario desde la medianoche (0 - 23).|
|**tm_mday**|Día del mes (1 - 31).|
|**tm_mon**|Mes (0 - 11; Enero n.o 0).|
|**tm_year**|Año (año actual menos 1900).|
|**tm_wday**|Día de la semana (0 - 6; Domingo 0).|
|**tm_yday**|Día del año (0 - 365; 1 de enero a 0).|
|**tm_isdst**|Valor positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; valor negativo si se desconoce el estado del horario de verano.|

Si se establece la variable de entorno **TZ,** la biblioteca en tiempo de ejecución de C asume las reglas adecuadas para los Estados Unidos para implementar el cálculo del horario de verano (DST).

## <a name="remarks"></a>Observaciones

La función **localtime** convierte una hora almacenada como un valor [de time_t](../../c-runtime-library/standard-types.md) y almacena el resultado en una estructura de tipo [tm](../../c-runtime-library/standard-types.md). El valor **long** *sourceTime* representa los segundos transcurridos desde la medianoche (00:00:00), 1 de enero de 1970, UTC. Este valor se obtiene normalmente de la función [de tiempo.](time-time32-time64.md)

Las versiones de 32 bits y 64 bits de [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)y **localtime** utilizan una única estructura **tm** por subproceso para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

**localtime** corrige la zona horaria local si el usuario establece primero la variable de entorno global **TZ**. Cuando se establece **TZ,** otras tres variables de entorno (**_timezone**, **_daylight**y **_tzname**) también se establecen automáticamente. Si no se establece la variable **TZ,** **localtime** intenta utilizar la información de zona horaria especificada en la aplicación Fecha/Hora en el Panel de control. Si no se puede obtener esta información, se usa de forma predeterminada PST8PDT, que significa la zona horaria del Pacífico. Vea [_tzset](tzset.md) para obtener una descripción de estas variables. **TZ** es una extensión de Microsoft y no forma parte de la definición estándar ANSI de **localtime**.

> [!NOTE]
> El entorno de destino debería intentar determinar si el horario de verano está vigente.

Estas funciones validan sus parámetros. Si *sourceTime* es un puntero nulo, o si el valor *sourceTime* es negativo, estas funciones invocan un controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven **NULL** y **establecen errno en** **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C necesario|Encabezado C++ necesario|
|-------------|---------------------|-|
|**hora local,** **_localtime32**, **_localtime64**|\<time.h>|\<ctime> \<o time.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
