---
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: 48d1104d9680fe8ab88f0f73bfc179f3e4cf45a6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919065"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Convierte la hora local en un valor de calendario.

## <a name="syntax"></a>Sintaxis

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parámetros

*timeptr*<br/>
Puntero a la estructura de hora; vea [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Valor devuelto

**_mktime32** devuelve la hora de calendario especificada codificada como un valor de tipo [time_t](../../c-runtime-library/standard-types.md). Si *timeptr* hace referencia a una fecha anterior a la medianoche del 1 de enero de 1970, o si no se puede representar la hora del calendario, **_mktime32** devuelve-1 convertido al tipo **time_t**. Cuando se usa **_mktime32** y si *timeptr* hace referencia a una fecha 23:59:59 posterior al 18 de enero de 2038, hora universal coordinada (UTC), devolverá-1 convertido al tipo **time_t**.

**_mktime64** devolverá-1 convertido al tipo **__time64_t** si *timeptr* hace referencia a una fecha posterior al 23:59:59 de diciembre de 3000, hora UTC.

## <a name="remarks"></a>Observaciones

Las funciones **mktime**, **_mktime32** y **_mktime64** convierten la estructura de tiempo proporcionada (posiblemente incompleta) a la que apunta *timeptr* en una estructura totalmente definida con valores normalizados y, a continuación, la convierte en un valor de hora **time_t** calendario. El tiempo convertido tiene la misma codificación que los valores devueltos por la función [time](time-time32-time64.md). Los valores originales de los componentes **tm_wday** y **tm_yday** de la estructura *timeptr* se omiten, y los valores originales de los demás componentes no están restringidos a sus intervalos normales.

**mktime** es una función insertada equivalente a **_mktime64**, a menos que se defina **_USE_32BIT_TIME_T** , en cuyo caso es equivalente a **_mktime32**.

Después de un ajuste a la hora UTC, **_mktime32** controla las fechas desde la medianoche del 1 de enero de 1970 23:59:59 hasta el 18 de enero de 2038, UTC. **_mktime64** controla las fechas desde la medianoche del 1 de enero de 1970 al 23:59:59, el 31 de diciembre de 3000. Este ajuste puede hacer que estas funciones devuelvan-1 (conversión a **time_t**, **__time32_t** o **__time64_t**) aunque la fecha especificada esté dentro del intervalo. Por ejemplo, si se encuentra en El Cairo (Egipto), que va dos horas por delante de UTC, primero se restarán dos horas de la fecha que especifique en *timeptr*, lo que puede poner la fecha fuera del intervalo.

Estas funciones se pueden usar para validar y rellenar una estructura de tm. Si se ejecutan correctamente, estas funciones establecen los valores de **tm_wday** y **tm_yday** según sea necesario y establecen los demás componentes para representar la hora de calendario especificada, pero con sus valores forzados a los intervalos normales. El valor final de **tm_mday** no se establece hasta que se determinan **tm_mon** y **tm_year** . Al especificar una hora de estructura de **TM** , establezca el campo de **tm_isdst** en:

- Cero (0) para indicar que está vigente la hora estándar.

- Un valor mayor que 0 para indicar que está vigente el horario de verano.

- Un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano.

La biblioteca en tiempo de ejecución de C determinará el comportamiento del horario de verano partiendo de la variable de entorno [TZ](tzset.md). Si no se establece **TZ** , la llamada a [GETTIMEZONEINFORMATION](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) de la API Win32 se usa para obtener la información del horario de verano del sistema operativo. Si se produce un error, la biblioteca supone que se usan las reglas de Estados Unidos para implementar el cálculo del horario de verano. **tm_isdst** es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de estas funciones es imprevisible. Si *timeptr* apunta a una estructura **TM** devuelta por una llamada anterior [a asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)o [localtime](localtime-localtime32-localtime64.md) (o las variantes de estas funciones), el campo **tm_isdst** contiene el valor correcto.

Tenga en cuenta que **gmtime** y **localtime** (y **_gmtime32**, **_gmtime64**, **_localtime32**y **_localtime64**) usan un único búfer por subproceso para la conversión. Si proporciona este búfer a **mktime**, **_mktime32** o **_mktime64**, se destruye el contenido anterior.

Estas funciones validan su parámetro. Si *timeptr* es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven-1 y establecen **errno** en **EINVAL**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Consulta también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
