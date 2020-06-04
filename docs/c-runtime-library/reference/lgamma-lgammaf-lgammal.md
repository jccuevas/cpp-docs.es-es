---
title: lgamma, lgammaf, lgammal
ms.date: 4/2/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: a610b0412b7e10949a810f4e360686292cff9ee3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916443"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Determina el logaritmo natural del valor absoluto de la función gamma del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor que se va a calcular.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el logaritmo natural del valor absoluto de la función gamma de *x*.

|Problema|Valor devuelto|
|-----------|------------|
|*x* = Nan|NaN|
|*x* = ± 0|+INFINITY|
|*x*= entero negativo|+INFINITY|
|± INFINITO|+INFINITY|
|error de polo|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|
|error de intervalo de desbordamiento|± HUGE_VAL, ± HUGE_VALF o ± HUGE_VALL|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Observaciones

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **lgamma (** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **lgamma (** siempre toma y devuelve un **valor Double**.

Si x es un número racional, esta función devuelve el logaritmo del factorial de (x-1).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**lgamma (**, **lgammaf (**, **lgammal**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
