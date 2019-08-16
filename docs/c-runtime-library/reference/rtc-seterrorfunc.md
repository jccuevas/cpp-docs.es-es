---
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
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
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 6b292d685eea8eccb9e9b2a3c3e6cd903d501005
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357214"
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

Designa una función como el controlador para notificar comprobaciones de errores en tiempo de ejecución (RTC). Esta función está en desuso; usar **_RTC_SetErrorFuncW** en su lugar.

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

No use esta función; en su lugar, use **_RTC_SetErrorFuncW**. Se conserva solo por motivos de compatibilidad con versiones anteriores.

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
