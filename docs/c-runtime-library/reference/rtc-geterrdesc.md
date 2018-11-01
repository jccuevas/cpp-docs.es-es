---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
apiname:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: d164626ea89bbe10f5b2ffe4224bf6381e40bab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590312"
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc

Devuelve una breve descripción de un tipo de comprobación de error en tiempo de ejecución (RTC).

## <a name="syntax"></a>Sintaxis

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>Parámetros

*errnum*<br/>
Un número entre cero y el valor devuelto por **_RTC_NumErrors**menos uno.

## <a name="return-value"></a>Valor devuelto

Una cadena de caracteres que contiene una descripción breve de uno de los tipos de error que detectó el sistema de comprobación de errores en tiempo de ejecución. Si el error es menor que cero o mayor o igual que el valor devuelto por [_RTC_NumErrors](rtc-numerrors.md), **_RTC_GetErrDesc** devuelve **NULL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)<br/>
