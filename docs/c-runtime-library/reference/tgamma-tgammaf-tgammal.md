---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362504"
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

*X*<br/>
Valor para buscar el valor gamma de.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve la gamma de *x*.

Puede producirse un error de rango si la magnitud de *x* es demasiado grande o demasiado pequeña para el tipo de datos. Puede producirse un error de dominio o un error de intervalo si *x* <0.

|Problema|Valor devuelto|
|-----------|------------|
|x - 0|•INFINITY|
|x = entero negativo|NaN|
|x - -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|error de dominio|NaN|
|error de polo|HUGE_VAL, HUGE_VALF o HUGE_VALL|
|error de intervalo de desbordamiento|HUGE_VAL, HUGE_VALF o HUGE_VALL|
|error de intervalo de subdesbordamiento|el valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Observaciones

Dado que C++ permite la sobrecarga, puede llamar a sobrecargas de **tgamma** que toman y devuelven **tipos float** y **long** **double.** En un programa C, **tgamma** siempre toma y devuelve un **doble**.

Si x es un número natural, esta función devuelve el factorial de (x-1).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
