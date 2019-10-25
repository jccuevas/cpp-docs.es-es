---
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 6c1eff5920931aa3b72bf3dbc6232c371828b16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948921"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

Asocia un error que se detecta mediante comprobaciones de errores en tiempo de ejecución (RTC) con un tipo. El controlador de errores procesa cómo mostrar los errores del tipo especificado.

## <a name="syntax"></a>Sintaxis

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Parámetros

*errnum*<br/>
Un número entre cero y uno menos el valor devuelto por [_RTC_NumErrors](rtc-numerrors.md).

*ErrType*<br/>
Valor que se va a asignar a este elemento *errnum*. Por ejemplo, se podría usar **_CRT_ERROR**. Si usa _ **crtdbgreport** como controlador de errores, *ErrType* solo puede ser uno de los símbolos definidos en _ [crtsetreportmode](crtsetreportmode.md). Si tiene su propio controlador de errores ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), puede disponer de tantos elementos *ErrType*como elementos *errnum*haya.

Un *ErrType* de _RTC_ERRTYPE_IGNORE tiene un significado especial para _ **crtsetreportmode**; se omite el error.

## <a name="return-value"></a>Valor devuelto

Valor anterior *del tipo de error.*

## <a name="remarks"></a>Comentarios

De forma predeterminada, todos los errores se establecen en *ErrType* = 1, que corresponde a **_CRT_ERROR**. Para obtener más información sobre los tipos de errores predeterminados, como **_CRT_ERROR**, vea [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de comprobación de errores en tiempo de ejecución; vea [Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)<br/>
