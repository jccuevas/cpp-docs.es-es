---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
ms.date: 11/04/2016
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: fcd1e3fdcca37d7e5bb381c234a6d8555ce2766c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951669"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Convierte una hora UTC representada por un **struct** **TM** en una hora UTC representada por un tipo **time_t** .

## <a name="syntax"></a>Sintaxis

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Parámetros

*timeptr*<br/>
Puntero a la hora UTC como **struct** **TM** que se va a convertir.

## <a name="return-value"></a>Valor devuelto

Una cantidad de tipo **__time32_t** o **__time64_t** que representa el número de segundos transcurridos desde la medianoche del 1 de enero de 1970, en hora universal coordinada (UTC). Si la fecha está fuera del intervalo (vea la sección comentarios) o la entrada no se puede interpretar como una hora válida, el valor devuelto es-1.

## <a name="remarks"></a>Comentarios

Las funciones **_mkgmtime32** y **_mkgmtime64** convierten una hora UTC en un tipo **__time32_t** o **__time64_t** que representa la hora en UTC. Para convertir una hora local a la hora UTC, use **mktime**, **_mktime32**y **_mktime64** en su lugar.

**_mkgmtime** es una función insertada que se evalúa como **_mkgmtime64**y **time_t** es equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como el antiguo de 32 bits **time_t**, puede definir **_USE_32BIT_TIME_T**. Esto no se recomienda porque la aplicación puede producir un error después del 18 de enero de 2038 (el intervalo máximo de un **time_t**de 32 bits) y no se permite en las plataformas de 64 bits.

La estructura de tiempo pasada se cambiará como sigue, de la misma manera en que se cambian con las funciones **_mktime** : los **campos tm_wday** y **tm_yday** se establecen en nuevos valores basados en los valores de **tm_mday** y **tm_year**. Al especificar una hora de la estructura **TM** , establezca el campo **tm_isdst** en:

- Cero (0) para indicar que está vigente la hora estándar.

- Un valor mayor que 0 para indicar que está vigente el horario de verano.

- Un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano.

La biblioteca en tiempo de ejecución de C usa la variable de entorno TZ para determinar el horario de verano correcto. Si TZ no está establecido, se consulta al sistema operativo para obtener el comportamiento correcto del horario de verano regional. **tm_isdst** es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de **mktime** es imprevisible.

El intervalo de la función **_mkgmtime32** va desde la medianoche del 1 de enero de 1970, hora utc a 23:59:59 el 18 de enero de 2038, UTC. El intervalo de **_mkgmtime64** va desde la medianoche del 1 de enero de 1970, utc a 23:59:59, 31 de diciembre de 3000, UTC. Una fecha fuera del intervalo da como resultado un valor devuelto de-1. El intervalo de **_mkgmtime** depende de si se define **_USE_32BIT_TIME_T** . Si no se define (valor predeterminado), el intervalo es el de **_mkgmtime64**; de lo contrario, el intervalo se limita al intervalo de 32 bits de **_mkgmtime32**.

Tenga en cuenta que **gmtime** y **localtime** usan un solo búfer asignado estáticamente para la conversión. Si proporciona este búfer a **mkgmtime**, se destruye el contenido anterior.

## <a name="example"></a>Ejemplo

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

En el ejemplo siguiente se muestra cómo se rellena la estructura incompleta con los valores calculados del día de la semana y el día del año.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

### <a name="output"></a>Resultados

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
