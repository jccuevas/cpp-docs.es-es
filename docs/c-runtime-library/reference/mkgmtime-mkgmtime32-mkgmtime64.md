---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: Describe las funciones de la biblioteca en tiempo de ejecución de _mkgmtime, _mkgmtime32 y _mkgmtime64 y proporciona ejemplos de cómo usarlas.
ms.date: 12/04/2019
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
ms.openlocfilehash: 3d03fc62853705a68e1a2e408d6af833e8c6b02b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857741"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Convierte una hora UTC representada por un **struct** **TM** en una hora UTC representada por un tipo de **time_t** .

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

### <a name="parameters"></a>Parameters

\ *timeptr*
Puntero a la hora UTC como **struct** **TM** que se va a convertir.

## <a name="return-value"></a>Valor devuelto

Cantidad de tipo **__time32_t** o **__time64_t** que representa el número de segundos transcurridos desde la medianoche del 1 de enero de 1970, en hora universal coordinada (UTC). Si la fecha está fuera del intervalo (vea la sección comentarios) o la entrada no se puede interpretar como una hora válida, el valor devuelto es-1.

## <a name="remarks"></a>Notas

Las funciones **_mkgmtime32** y **_mkgmtime64** convierten una hora UTC en un tipo de **__time32_t** o **__time64_t** que representa la hora en UTC. Para convertir una hora local a la hora UTC, use **mktime**, **_mktime32**y **_mktime64** en su lugar.

**_mkgmtime** es una función insertada que se evalúa como **_mkgmtime64**y **time_t** es equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como la **time_t**de 32 bits anterior, puede definir **_USE_32BIT_TIME_T**. No se recomienda porque la aplicación puede producir un error después del 18 de enero de 2038, el intervalo máximo de un **time_t**de 32 bits. No está permitida en las plataformas de 64 bits.

La estructura de tiempo pasada se cambia como se indica a continuación, de la misma manera en que la **_mktime** funciones: los campos **tm_wday** y **tm_yday** se establecen en nuevos valores basados en los valores de **tm_mday** y **tm_year**. Dado que se supone que la hora es UTC, se omite el campo **tm_isdst** .

El intervalo de la función **_mkgmtime32** va desde la medianoche del 1 de enero de 1970, hora utc a 23:59:59 del 18 de enero de 2038, UTC. El intervalo de **_mkgmtime64** va desde la medianoche del 1 de enero de 1970, utc a 23:59:59, 31 de diciembre de 3000, UTC. Una fecha fuera del intervalo da como resultado un valor devuelto de-1. El intervalo de **_mkgmtime** depende de si se define **_USE_32BIT_TIME_T** . Cuando no se define, que es el valor predeterminado, el intervalo es igual que **_mkgmtime64**. De lo contrario, el intervalo se limita al intervalo de 32 bits de **_mkgmtime32**.

Tanto **gmtime** como **localtime** usan un búfer estático común para la conversión. Si proporciona este búfer a **_mkgmtime**, se destruye el contenido anterior.

## <a name="examples"></a>Ejemplos

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

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

En el ejemplo siguiente se muestra cómo rellenar la estructura incompleta mediante **_mkgmtime**. Calcula valores para el día de la semana y para el año.

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

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)
