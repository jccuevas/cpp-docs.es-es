---
title: exp2, exp2f, exp2l
ms.date: 04/05/2018
api_name:
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 89e0448501cbd423278607bb22959c6cd1ed9464
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941564"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Calcula 2 elevado al valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor del exponente.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el exponente de base 2 de *x*, es decir, 2<sup>x</sup>. De lo contrario, devuelve uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = ±0|1|
|*x* = -INFINITY|+0|
|*x* = infinito|+INFINITY|
|*x* = Nan|NaN|
|Error de intervalo de desbordamiento|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|
|Error de intervalo de subdesbordamiento|Resultado correcto, después del redondeo|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **exp2** que toman y devuelven los tipos **float** y **Long Double** . En un programa de C, **exp2** siempre toma y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**exp**, **expf**, **expl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
