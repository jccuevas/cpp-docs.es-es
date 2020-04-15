---
title: _get_dstbias
ms.date: 4/2/2020
api_name:
- _get_dstbias
- __dstbias
- _o___dstbias
- _o__get_dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 969b6d2dfd83a1a136fdfb3d17f8f843337b792c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345226"
---
# <a name="_get_dstbias"></a>_get_dstbias

Recupera el desplazamiento de horario de verano en segundos.

## <a name="syntax"></a>Sintaxis

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parámetros

*Segundos*<br/>
Desplazamiento en segundos del horario de verano.

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente o un valor **errno** si se produce un error.

## <a name="remarks"></a>Observaciones

La función **_get_dstbias** recupera el número de segundos en el horario de verano como un entero. Si el horario de verano está en vigor, el desplazamiento predeterminado es de 3600 segundos, que es la cantidad de segundos que hay en una hora (si bien en algunas regiones el desplazamiento es de dos horas).

Si *seconds* es **NULL**, se invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **EINVAL**.

Le recomendamos que utilice esta función en lugar de la **_dstbias** de macro o la función en desuso **__dstbias**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
