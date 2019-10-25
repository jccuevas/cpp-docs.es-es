---
title: _scalb, _scalbf
ms.date: 04/05/2018
api_name:
- _scalb
- _scalbf
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: 630a5e3db2c39cb40d31c71e6a6dfa214ed91e34
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948884"
---
# <a name="_scalb-_scalbf"></a>_scalb, _scalbf

Escala el argumento por una potencia de 2.

## <a name="syntax"></a>Sintaxis

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante de precisión doble.

*exp*<br/>
Exponente de entero largo.

## <a name="return-value"></a>Valor devuelto

Devuelve un valor exponencial si es correcto. En el desbordamiento (dependiendo del signo de *x*), **_scalb** devuelve +/- **HUGE_VAL**; la variable **errno** se establece en **ERANGE**.

Para más información sobre este y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_scalb** calcula el valor de *x* \* 2<sup>*exp*</sup>.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_scalb**, **_scalbf**|\<float.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
