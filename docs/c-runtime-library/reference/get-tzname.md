---
title: _get_tzname | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_tzname
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
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b49aa404dda6234382ae461459dece64e5996d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="gettzname"></a>_get_tzname

Recupera la representación de cadena de caracteres del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST).

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
La longitud de cadena de *timeZoneName* incluido un terminador nulo.

*timeZoneName*<br/>
La dirección de una cadena de caracteres para la representación del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST), dependiendo de *índice*.

*sizeInBytes*<br/>
El tamaño de la *timeZoneName* en bytes de la cadena de caracteres.

*index*<br/>
Índice de uno de los dos nombres de zona horaria que se van a recuperar.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto, en caso contrario, un **errno** tipo de valor.

Si el valor *timeZoneName* es **NULL**, o *sizeInBytes* es cero o menor que cero (pero no ambos), se invoca un controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Valor devuelto|Contenido de *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|tamaño de nombre de ZH|**NULL**|0|0 o 1|0|no modificado|
|tamaño de nombre de ZH|any|> 0|0 o 1|0|Nombre de ZH|
|no modificado|**NULL**|> 0|any|**EINVAL**|no modificado|
|no modificado|any|cero|any|**EINVAL**|no modificado|
|no modificado|any|> 0|> 1|**EINVAL**|no modificado|

## <a name="remarks"></a>Comentarios

El **_get_tzname** función recupera la representación de cadena de caracteres del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST) en la dirección de *timeZoneName* según el índice valor, así como el tamaño de la cadena en *pReturnValue*. Si *timeZoneName* es **NULL** y *sizeInBytes* es cero, el tamaño de la cadena de hora zona en bytes se devuelve en *pReturnValue*. Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona de hora estándar de horario de verano; todos los demás valores de índice tienen resultados indeterminados.

### <a name="index-values"></a>Valores de índice

|*index*|Contenido de *timeZoneName*|*timeZoneName* valor predeterminado|
|-------------|--------------------------------|----------------------------------|
|0|Nombre de zona horaria|"PST"|
|1|Nombre de zona de hora estándar de horario de verano|"PDT"|
|> 1 o < 0|**errno** establecido en **EINVAL**|no modificado|

A menos que los valores se cambien explícitamente durante el tiempo de ejecución, los valores predeterminados son "PST" y "PDT", respectivamente.  Los tamaños de estas matrices de caracteres se rigen por **TZNAME_MAX** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
