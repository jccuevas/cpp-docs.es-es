---
title: _RTC_SetErrorFunc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorFunc
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
apitype: DLLExport
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs:
- C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e146f699f9026260470b1c540c7567f074896a38
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

Designa una función como el controlador para notificar comprobaciones de errores en tiempo de ejecución (RTC). Esta función está desusada; usar **_RTC_SetErrorFuncW** en su lugar.

## <a name="syntax"></a>Sintaxis

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Parámetros

*function*<br/>
La dirección de la función que controlará las comprobaciones de errores en tiempo de ejecución.

## <a name="return-value"></a>Valor devuelto

La función de error definida previamente. Si no hay ninguna función definida previamente, devuelve **NULL**.

## <a name="remarks"></a>Comentarios

No utilice esta función; en su lugar, use **_RTC_SetErrorFuncW**. Se conserva solo por motivos de compatibilidad con versiones anteriores.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)<br/>
