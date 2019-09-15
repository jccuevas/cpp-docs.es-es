---
title: log2, log2f, log2l
ms.date: 04/05/2018
api_name:
- log2
- log2l
- log2f
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: bf1734ea2f96fa1c09b3b0d1f43b681fc31c8f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953168"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Determina el logaritmo binario (base 2) del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
El valor del que se determina el logaritmo de base 2.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve devolverá LOG2 *x*.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|error de dominio|NaN|
|error de polo|-HUGE_VAL, -HUGE_VALF o -HUGE_VALL|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Si x es un entero, esta función devuelve esencialmente el índice de base cero del valor de 1 bit más significativo de *x*.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log2**, **log2f**, **log2l**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
