---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: ca514c60945f25c3d335e0b02110e50ed14f9269
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911816"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Establece el intervalo al que apunta el primer argumento en la hora actual del calendario, basándose en la base de tiempo especificada.

## <a name="syntax"></a>Sintaxis

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>Parámetros

*time_spec*<br/>
Puntero para una estructura que se establece en el tiempo en segundos y nanosegundos desde el inicio de la época.

*base*<br/>
Un valor específico de implementación distinta de cero que especifica la base de tiempo.

## <a name="return-value"></a>Valor devuelto

El valor de *base* si es correcto; de lo contrario, devuelve cero.

## <a name="remarks"></a>Observaciones

Las funciones de **timespec_get** establecen la hora actual en la estructura a la que apunta el argumento *time_spec* . Todas las versiones de este struct tienen dos miembros, **tv_sec** y **tv_nsec**. El valor **tv_sec** se establece en el número entero de segundos y **tv_nsec** en el número entero de nanosegundos, redondeado a la resolución del reloj del sistema, desde el inicio del tiempo especificado por *base*.

**Específicos de Microsoft**

Estas funciones solo admiten **TIME_UTC** como valor *base* . Esto establece el valor de *time_spec* en el número de segundos y nanosegundos desde el inicio de la época, medianoche, el 1 de enero de 1970, hora universal coordinada (UTC). En una **struct** **_timespec32**de struct, **tv_sec** es un valor de **__time32_t** . En una **struct** **_timespec64**de struct, **tv_sec** es un valor de **__time64_t** . En una **estructura** **timespec**, **tv_sec** es un tipo de **time_t** , que tiene una longitud de 32 bits o 64 bits, en función de si se define la macro de preprocesador _USE_32BIT_TIME_T. La función **timespec_get** es una función insertada que llama a **_timespec32_get** si se define _USE_32BIT_TIME_T; en caso contrario, llama a **_timespec64_get**.

**Finalizar específico de Microsoft**

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h>, C++: \<ctime> o \<time.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
