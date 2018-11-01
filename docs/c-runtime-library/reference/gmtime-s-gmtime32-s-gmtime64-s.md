---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 11/04/2016
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 1d9bfc7858dbc718e0f6c07358c5ebcec546063e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650013"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Convierte un valor de tiempo en un **tm** estructura. Estas son versiones de [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Parámetros

*tmDest*<br/>
Puntero a un [tm](../../c-runtime-library/standard-types.md) estructura. Los campos de la estructura devuelta contienen el valor evaluado de la *temporizador* argumento en UTC en lugar de en la hora local.

*sourceTime*<br/>
Puntero a la hora almacenada. La hora se representa como los segundos transcurridos desde la medianoche (00:00:00) del 1 de enero de 1970, hora universal coordinada (UTC).

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h; para obtener una lista de estos errores, vea [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Condiciones de error

|*tmDest*|*sourceTime*|Volver|Valor de *tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|any|**EINVAL**|No modificado.|
|No **NULL** (apunta a la memoria válida)|**NULL**|**EINVAL**|Todos los campos establecidos en -1.|
|No **NULL**|< 0|**EINVAL**|Todos los campos establecidos en -1.|

En el caso de las dos primeras condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EINVAL**.

## <a name="remarks"></a>Comentarios

El **_gmtime32_s** función divide la *sourceTime* valor y lo almacena en una estructura de tipo **tm**, definida en Time.h. La dirección de la estructura se pasa en *tmDest*. El valor de *sourceTime* suele obtenerse de una llamada a la [tiempo](time-time32-time64.md) función.

> [!NOTE]
> El entorno de destino debería intentar determinar si el horario de verano está vigente. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano.

Cada uno de los campos de la estructura es de tipo **int**, tal y como se muestra en la tabla siguiente.

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
|**tm_isdst**|Siempre es 0 para **gmtime_s**.|

**_gmtime64_s**, que usa el **__time64_t** estructura, permite fechas expresarse a través de 23:59:59, 31 de diciembre de 3000, UTC; mientras que **gmtime32_s** solo representan fechas hasta las 23:59:59 del 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para ambas funciones.

**gmtime_s** es una función insertada que se evalúa como **_gmtime64_s** y **time_t** es equivalente a **__time64_t**. Si necesita forzar el compilador interprete **time_t** como el antiguo 32-bit **time_t**, puede definir **_USE_32BIT_TIME_T**. Al hacerlo, **gmtime_s** se inserte en **_gmtime32_s**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C necesario|Encabezado C++ necesario|
|-------------|---------------------|-|
|**gmtime_s**|, **_gmtime32_s**, **_gmtime64_s**|\<time.h>|\<CTime > o \<time.h >|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
