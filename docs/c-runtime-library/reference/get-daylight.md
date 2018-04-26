---
title: _get_daylight | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- __daylight
- _get_daylight
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
- get_daylight
- _get_daylight
dev_langs:
- C++
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9df76bb56ace99f4242c31d843274cc30628eccf
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="getdaylight"></a>_get_daylight

Recupera el desplazamiento de horario de verano en horas.

## <a name="syntax"></a>Sintaxis

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parámetros

*Horas*<br/>
Desplazamiento en horas del horario de verano.

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente, o un **errno** valor si se produce un error.

## <a name="remarks"></a>Comentarios

El **_get_daylight** función recupera el número de horas en el horario de verano como un entero. Si el horario de verano está en vigor, el desplazamiento predeterminado es de una hora (si bien en algunas regiones el desplazamiento es de dos horas).

Si *horas* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

Se recomienda usar esta función en lugar de la macro **_daylight** o la función en desuso **__daylight**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
