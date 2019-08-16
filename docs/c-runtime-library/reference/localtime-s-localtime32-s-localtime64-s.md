---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 07/09/2019
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
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: 454ab492fbe8a31b9ceeca518fa5e590271dbf06
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693413"
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

Convierte un **time_t** tiempo valor a un **tm** estructurar y lo corrige para la zona horaria local. Estas son versiones de [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>Parámetros

*tmDest*<br/>
Puntero a la estructura de tiempo que debe rellenarse.

*sourceTime*<br/>
Puntero a la hora almacenada.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, vea [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|*tmDest*|*sourceTime*|Valor devuelto|Valor de *tmDest*|Invoca el controlador de parámetros no válidos|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|any|**EINVAL**|No modificado|Sí|
|No **NULL** (apunta a la memoria válida)|**NULL**|**EINVAL**|Todos los campos establecidos en -1|Sí|
|No **NULL** (apunta a la memoria válida)|menor que 0 o mayor que **_MAX__TIME64_T**|**EINVAL**|Todos los campos establecidos en -1|No|

En el caso de las dos primeras condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EINVAL**.

## <a name="remarks"></a>Comentarios

El **localtime_s** función convierte una hora almacenada como un [time_t](../../c-runtime-library/standard-types.md) de valor y almacena el resultado en una estructura de tipo [tm](../../c-runtime-library/standard-types.md). El **time_t** valor *sourceTime* representa los segundos transcurridos desde la medianoche (00: 00:00) del 1 de enero de 1970, UTC. Este valor suele obtenerse de la [tiempo](time-time32-time64.md) función.

**localtime_s** corrige la zona horaria local si el usuario establece primero la variable de entorno global **TZ**. Cuando **TZ** está establecida, otras tres variables de entorno ( **_timezone**, **_daylight**, y **_tzname**) se establecen automáticamente también. Si el **TZ** no se establece la variable, **localtime_s** intenta usar la información de zona horaria especificada en la aplicación de fecha y hora en el Panel de Control. Si no se puede obtener esta información, se usa de forma predeterminada PST8PDT, que significa la zona horaria del Pacífico. Vea [_tzset](tzset.md) para obtener una descripción de estas variables. **TZ** es una extensión de Microsoft y no forma parte de la definición del estándar ANSI de **localtime**.

> [!NOTE]
> El entorno de destino debería intentar determinar si el horario de verano está vigente.

**_localtime64_s**, que usa el **__time64_t** estructura, permite expresar hasta las 23:59:59, 18 de enero, 3001, hora universal coordinada (UTC), fechas, mientras que **_localtime32_s** representa fechas hasta las 23:59:59 del 18 de enero de 2038, UTC.

**localtime_s** es una función insertada que se evalúa como **_localtime64_s**, y **time_t** es equivalente a **__time64_t**. Si necesita forzar el compilador interprete **time_t** como el antiguo 32-bit **time_t**, puede definir **_USE_32BIT_TIME_T**. Al hacerlo, **localtime_s** se evalúe como **_localtime32_s**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

Los campos de tipo de estructura [tm](../../c-runtime-library/standard-types.md) almacenar los valores siguientes, cada uno de los cuales es un **int**.

|Campo|Descripción|
|-|-|
|**tm_sec**|Segundos después del minuto (0 - 59).|
|**tm_min**|Minutos después de la hora (0 - 59).|
|**tm_hour**|Horas desde medianoche (0 - 23).|
|**tm_mday**|Día del mes (1-31).|
|**tm_mon**|Mes (0 - 11; Enero = 0).|
|**tm_year**|Año (año actual menos 1900).|
|**tm_wday**|Día de la semana (0 - 6; El domingo = 0).|
|**tm_yday**|Día del año (0 - 365; El 1 de enero = 0).|
|**tm_isdst**|Valor positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; valor negativo si se desconoce el estado del horario de verano.|

Si el **TZ** se establece la variable de entorno, la biblioteca de tiempo de ejecución de C usa las reglas correspondientes a Estados Unidos para implementar el cálculo del horario de verano (DST).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C necesario|Encabezado C++ necesario|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<CTime > o \<time.h >|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

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
        newtime.tm_hour -= 12;        // to 12-hour clock.
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

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
