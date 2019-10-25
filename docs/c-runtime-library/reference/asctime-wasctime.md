---
title: asctime, _wasctime
ms.date: 11/04/2016
api_name:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: 9ca9bbcbfff3d2bef41443ff1744a1b612727c20
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939670"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Convierte una estructura de tiempo de **TM** en una cadena de caracteres. Hay disponibles versiones más seguras de estas funciones; consulte [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>Parámetros

*timeptr*<br/>
Estructura de fecha y hora.

## <a name="return-value"></a>Valor devuelto

**asctime** devuelve un puntero al resultado de la cadena de caracteres; **_wasctime** devuelve un puntero al resultado de la cadena de caracteres anchos. No hay ningún error de valor devuelto.

## <a name="remarks"></a>Comentarios

Hay disponibles versiones más seguras de estas funciones; consulte [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

La función **asctime** convierte una hora almacenada como una estructura en una cadena de caracteres. El valor de *timeptr* se suele obtener de una llamada a **gmtime** o **localtime**, que devuelven un puntero a una estructura de **TM** , definidos en el tiempo. C.

|miembro de timeptr|Valor|
|--------------------|-----------|
|**tm_hour**|Horas desde la medianoche (0-23)|
|**tm_isdst**|Positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; negativo si se desconoce el estado del horario de verano. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).|
|**tm_mday**|Día del mes (1-31)|
|**tm_min**|Minutos después de la hora (0-59)|
|**tm_mon**|Mes (0-11; Enero = 0)|
|**tm_sec**|Segundos después del minuto (0-59)|
|**tm_wday**|Día de la semana (0-6; Sunday = 0)|
|**tm_yday**|Día del año (0-365; 1 de enero = 0)|
|**tm_year**|Año (año actual menos 1900)|

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Para obtener información sobre cómo configurar la hora local, vea las funciones [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md) y [localtime](localtime-localtime32-localtime64.md) y la función [_tzset](tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y variables globales.

El resultado de la cadena producido por **asctime** contiene exactamente 26 caracteres y tiene `Wed Jan 02 02:03:55 1980\n\0`el formato. Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea y el carácter nulo ocupan las dos últimas posiciones de la cadena. **asctime** usa un solo búfer asignado estáticamente para contener la cadena devuelta. Cada llamada a esta función destruye el resultado de la llamada anterior.

**_wasctime** es una versión con caracteres anchos de **asctime**. **_wasctime** y **asctime** se comportan de manera idéntica.

Estas funciones validan sus parámetros. Si *timeptr* es un puntero nulo, o si contiene valores fuera del intervalo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **null** y establece **errno** en **EINVAL**.

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> o \<wchar.h>|

## <a name="example"></a>Ejemplo

Este programa coloca la hora del sistema en el **aclock**entero largo, lo traduce en la estructura **newtime** y, a continuación, lo convierte en un formato de cadena para la salida, mediante la función **asctime** .

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
