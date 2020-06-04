---
title: gmtime, _gmtime32, _gmtime64
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 16f4315837873c8d78065ea97a11188bdddedbed
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916236"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Convierte un valor de hora de **time_t** en una estructura de **TM** . Hay disponibles versiones más seguras de estas funciones; vea [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Sintaxis

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parámetros

*sourceTime*<br/>
Puntero a la hora almacenada. La hora se representa como los segundos transcurridos desde la medianoche (00:00:00) del 1 de enero de 1970, hora universal coordinada (UTC).

## <a name="return-value"></a>Valor devuelto

Puntero a una estructura de tipo [tm](../../c-runtime-library/standard-types.md). Los campos de la estructura devuelta contienen el valor evaluado del argumento *sourceTime* en UTC en lugar de en la hora local. Cada uno de los campos de la estructura es de tipo **int**, como se indica a continuación:

|Campo|Descripción|
|-|-|
|**tm_sec**|Segundos después del minuto (0-59).|
|**tm_min**|Minutos después de la hora (0-59).|
|**tm_hour**|Horas desde la medianoche (0-23).|
|**tm_mday**|Día del mes (1-31).|
|**tm_mon**|Mes (0-11; Enero = 0).|
|**tm_year**|Año (año actual menos 1900).|
|**tm_wday**|Día de la semana (0-6; Sunday = 0).|
|**tm_yday**|Día del año (0-365; 1 de enero = 0).|
|**tm_isdst**|Siempre es 0 para **gmtime**.|

Tanto las versiones de 32 bits como las de 64 bits de **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)y [localtime](localtime-localtime32-localtime64.md) usan una estructura de **TM** común por subproceso para la conversión. Cada llamada a una de estas funciones destruye el resultado de las llamadas anteriores. Si *sourceTime* representa una fecha anterior a la medianoche del 1 de enero de 1970, **gmtime** devuelve **null**. No se devuelve ningún error.

**_gmtime64**, que usa la estructura de **__time64_t** , permite expresar fechas hasta el 23:59:59 de diciembre de 3000, hora utc, mientras que **_gmtime32** solo representan fechas 23:59:59 hasta el 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para ambas funciones.

**gmtime** es una función insertada que se evalúa como **_gmtime64**y **time_t** es equivalente a **__time64_t** a menos que se defina **_USE_32BIT_TIME_T** . Si debe obligar al compilador a interpretar **time_t** como la **time_t**de 32 bits anterior, puede definir **_USE_32BIT_TIME_T**, pero esto hace que **gmtime** se contengan alineados con **_gmtime32** y **time_t** se definirán como **__time32_t**. Esta operación no es recomendable, porque no se permite en plataformas de 64 bits y, en todo caso, la aplicación puede producir un error después del 18 de enero de 2038.

Estas funciones validan sus parámetros. Si *sourceTime* es un puntero nulo, o si el valor de *sourceTime* es negativo, estas funciones invocan un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven **null** y establecen **errno** en **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_gmtime32** divide el valor de *sourceTime* y lo almacena en una estructura asignada estáticamente de tipo **TM**, definida en el tiempo. C. El valor de *sourceTime* se suele obtener de una llamada a la función [Time](time-time32-time64.md) .

> [!NOTE]
> En la mayoría de los casos, el entorno de destino intenta determinar si está vigente el horario de verano. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C necesario|Encabezado C++ necesario|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<> ctime o \<Time. h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
