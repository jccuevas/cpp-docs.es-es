---
title: _get_timezone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_timezone
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
- _get_timezone
- get_timezone
dev_langs:
- C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111cbff00d1f6119fbd806cc5fc3d14c28a7d7c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398281"
---
# <a name="gettimezone"></a>_get_timezone

Recupera la diferencia en segundos entre la hora universal coordinada (UTC) y la hora local.

## <a name="syntax"></a>Sintaxis

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Parámetros

*Segundos*<br/>
Diferencia en segundos entre la hora UTC y la hora local.

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente, o un **errno** valor si se produce un error.

## <a name="remarks"></a>Comentarios

El **_get_timezone** función recupera la diferencia en segundos entre la hora UTC y la hora local como un número entero. El valor predeterminado es 28.800 segundos, hora del Pacífico (ocho horas por detrás de la hora UTC).

Si *segundos* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
