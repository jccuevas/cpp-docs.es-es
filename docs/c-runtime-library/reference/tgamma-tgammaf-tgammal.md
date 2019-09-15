---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946212"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Determina la función gamma del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor para buscar el valor gamma de.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el gamma de *x*.

Puede producirse un error de intervalo si la magnitud de *x* es demasiado grande o demasiado pequeña para el tipo de datos. Puede producirse un error de dominio o un error de intervalo si *x* < = 0.

|Problema|Volver|
|-----------|------------|
|x = ±0|± INFINITO|
|x = entero negativo|NaN|
|x = infinito|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|error de dominio|NaN|
|error de polo|± HUGE_VAL, ± HUGE_VALF o ± HUGE_VALL|
|error de intervalo de desbordamiento|± HUGE_VAL, ± HUGE_VALF o ± HUGE_VALL|
|error de intervalo de subdesbordamiento|el valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **tgamma** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **tgamma** siempre toma y devuelve un **valor Double**.

Si x es un número natural, esta función devuelve el factorial de (x-1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf (** , **tgammal**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
