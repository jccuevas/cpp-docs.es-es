---
title: timespec_get, _timespec32_get, _timespec64_get1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
dev_langs:
- C++
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f00a59f8b5813398b47562b106f3ec0eff3363b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412838"
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get, _timespec32_get, _timespec64_get

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

El valor de *base* si correcto; en caso contrario, devuelve cero.

## <a name="remarks"></a>Comentarios

El **timespec_get** funciones establecen la hora actual en la estructura que señala el *time_spec* argumento. Todas las versiones de esta estructura tienen dos miembros, **tv_sec** y **tv_nsec**. El **tv_sec** valor se establece en el número entero de segundos y **tv_nsec** en el número integral de nanosegundos, redondeado a la resolución del reloj del sistema, desde el inicio de la época especificada por *base*.

**Específicos de Microsoft**

Estas funciones solo admiten **TIME_UTC** como el *base* valor. Esto establece la *time_spec* valor para el número de segundos y nanosegundos desde el inicio de la época, medianoche del 1 de enero de 1970, hora Universal coordinada (UTC). En un **struct** **_timespec32**, **tv_sec** es un **__time32_t** valor. En un **struct** **_timespec64**, **tv_sec** es un **__time64_t** valor. En un **struct** **timespec**, **tv_sec** es un **time_t** tipo, que es de 32 bits o 64 bits de longitud, dependiendo de si el preprocesador se define _USE_32BIT_TIME_T de macro. El **timespec_get** función es una función insertada que llama **_timespec32_get** si se define _USE_32BIT_TIME_T; en caso contrario, llama **_timespec64_get**.

**Fin de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h>, C++: \<ctime> o \<time.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
