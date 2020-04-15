---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: Describe las funciones de biblioteca en tiempo de ejecución de _mkgmtime, _mkgmtime32 y _mkgmtime64 de C y proporciona ejemplos de cómo usarlas.
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338771"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Convierte una hora UTC representada por una **struct** **tm** a una hora UTC representada por un tipo **de time_t.**

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

*timeptr*\
Un puntero a la hora UTC como una **estructura** **tm** para convertir.

## <a name="return-value"></a>Valor devuelto

Una cantidad de **tipo __time32_t** o **__time64_t** que representa el número de segundos transcurridos desde la medianoche, 1 de enero de 1970, en la hora universal coordinada (UTC). Si la fecha está fuera del rango (consulte la sección Comentarios) o la entrada no se puede interpretar como una hora válida, el valor devuelto es -1.

## <a name="remarks"></a>Observaciones

Las funciones **_mkgmtime32** y **_mkgmtime64** convierten una hora UTC en un tipo **de __time32_t** o **__time64_t** que representa la hora en UTC. Para convertir una hora local a hora UTC, utilice **mktime**, **_mktime32**y **_mktime64** en su lugar.

**_mkgmtime** es una función en línea que se evalúa como **_mkgmtime64**y **time_t** equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como el **antiguo time_t**de 32 bits, puede definir **_USE_32BIT_TIME_T**. No se recomienda, ya que la aplicación podría fallar después del 18 de enero de 2038, el intervalo máximo de un **time_t**de 32 bits. No está permitido en absoluto en plataformas de 64 bits.

La estructura de tiempo que se pasa se cambia de la siguiente manera, de la misma manera que cambia las funciones **_mktime:** los campos **tm_wday** y **tm_yday** se establecen en nuevos valores en función de los valores de **tm_mday** y **tm_year**. Dado que se supone que la hora es UTC, se omite el campo **tm_isdst.**

El rango de la función **_mkgmtime32** es de medianoche, 1 de enero de 1970, UTC a 23:59:59 enero 18, 2038, UTC. El rango de **_mkgmtime64** es de medianoche, 1 de enero de 1970, UTC a 23:59:59, 31 de diciembre de 3000, UTC. Una fecha fuera del intervalo da como resultado un valor devuelto de -1. El intervalo de **_mkgmtime** depende de si se define **_USE_32BIT_TIME_T.** Cuando no está definido, que es el valor predeterminado, el intervalo es el mismo que **_mkgmtime64**. De lo contrario, el intervalo se limita al rango de 32 bits de **_mkgmtime32**.

Tanto **gmtime** como **localtime** utilizan un búfer estático común para la conversión. Si proporciona este búfer a **_mkgmtime**, se destruye el contenido anterior.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

En el ejemplo siguiente se muestra cómo se rellena la estructura incompleta con **_mkgmtime**. Calcula los valores para el día de la semana y del año.

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

## <a name="see-also"></a>Consulte también

[Gestión del tiempo](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)
