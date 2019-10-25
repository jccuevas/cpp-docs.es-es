---
title: _get_dstbias
ms.date: 11/04/2016
api_name:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: a48cc4fe35a1bbd18342750571214ed0977cf3ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955952"
---
# <a name="_get_dstbias"></a>_get_dstbias

Recupera el desplazamiento de horario de verano en segundos.

## <a name="syntax"></a>Sintaxis

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parámetros

*s*<br/>
Desplazamiento en segundos del horario de verano.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto o un valor **errno** si se produce un error.

## <a name="remarks"></a>Comentarios

La función **_get_dstbias** recupera el número de segundos en el horario de verano como un entero. Si el horario de verano está en vigor, el desplazamiento predeterminado es de 3600 segundos, que es la cantidad de segundos que hay en una hora (si bien en algunas regiones el desplazamiento es de dos horas).

Si el valor de *seconds* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

Se recomienda usar esta función en lugar de la macro **_dstbias** o la función desusada **__dstbias**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
