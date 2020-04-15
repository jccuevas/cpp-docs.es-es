---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: 0ffd779d8c74b64403837bd973b025da7e3fac2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345551"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Obtiene la hora actual. Se trata de versiones de [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parámetros

*timeptr*<br/>
Puntero a una estructura **_timeb**, **__timeb32**o **__timeb64.**

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *timeptr* es **NULL**, el valor devuelto es **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_ftime_s** obtiene la hora local actual y la almacena en la estructura señalada por *timeptr*. Las estructuras **_timeb**, **__timeb32**y **__timeb64** se definen en SYS-Timeb.h. Contienen cuatro campos, que se enumeran en la tabla siguiente.

|Campo|Descripción|
|-|-|
|**dstflag**|Distinto de cero si el horario de verano está en vigor para la zona horaria local. (Consulte [_tzset](tzset.md) para obtener una explicación de cómo se determina el horario de verano).|
|**millitm**|Fracción de segundo en milisegundos.|
|**time**|La hora en segundos desde la medianoche (00:00:00) del 1 de enero de 1970, hora universal coordinada (UTC).|
|**Timezone**|Diferencia en minutos, que se desplaza hacia el oeste, entre la hora UTC y la hora local. El valor de **zona horaria** se establece a partir del valor de la variable global **_timezone** (consulte **_tzset**).|

La función **_ftime64_s,** que utiliza la estructura **__timeb64,** permite que las fechas de creación de archivos se expresen hasta las 23:59:59, 31 de diciembre de 3000, UTC; mientras **que _ftime32_s** sólo representa fechas hasta las 23:59:59 del 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.

La función **_ftime_s** es equivalente a **_ftime64_s**y **_timeb** contiene un tiempo de 64 bits, a menos que se defina **_USE_32BIT_TIME_T,** en cuyo caso el comportamiento anterior está en vigor; **_ftime_s** utiliza un tiempo de 32 bits y **_timeb** contiene un tiempo de 32 bits.

**_ftime_s** valida sus parámetros. Si se pasa un puntero nulo como *timeptr*, la función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece **errno en** **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> y \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> y \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> y \<sys/timeb.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime64_s( &timebuffer );

    time1 = timebuffer.time;
    millitm1 = timebuffer.millitm;
    timezone1 = timebuffer.timezone;
    dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
