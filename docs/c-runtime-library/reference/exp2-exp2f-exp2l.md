---
title: exp2, exp2f, exp2l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- exp2
- exp2f
- exp2l
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs:
- C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aea847d367200635c8fecbd694f8a50be859b3ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396727"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Calcula 2 elevado en el valor especificado.

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

Si se realiza correctamente, devuelve el exponente de base 2 de *x*, es decir, 2<sup>x</sup>. En caso contrario, devuelve uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = ± 0|1|
|*x* = - infinito|+0|
|*x* = + infinito|+INFINITY|
|*x* = NaN|NaN|
|Error de intervalo de desbordamiento|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|
|Error de intervalo de subdesbordamiento|Resultado correcto, después de redondearlo|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **exp2** que toman y devuelven **float** y **long double** tipos. En un programa C, **exp2** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**EXP**, **expf**, **expl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
