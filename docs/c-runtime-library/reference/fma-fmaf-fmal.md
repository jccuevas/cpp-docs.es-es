---
title: fma, fmaf, fmal
ms.date: 4/2/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: 993ca4d57202b3789929161a964b3e41d48fd98f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346569"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Multiplica dos valores juntos, agrega un tercer valor y luego redondea el resultado, sin perder ninguna precisión debido al redondeo intermedio.

## <a name="syntax"></a>Sintaxis

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Primer valor que se va a multiplicar.

*y y*<br/>
Segundo valor que se va a multiplicar.

*Z*<br/>
El valor que se va a agregar.

## <a name="return-value"></a>Valor devuelto

Devuelve `(x * y) + z`. El valor devuelto se redondea después con el formato de redondeo actual.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Valor devuelto|
|-----------|------------|
|*x* - INFINITY, *y* á 0 o<br /><br /> *x* - 0, *y* - INFINITY|NaN|
|*x* o *y* - exacto s/ INFINITO, *z* - INFINITY con el signo opuesto|NaN|
|*x* o *y* - NaN|NaN|
|no (*x* - 0, *y*- indefinido) y *z* - NaN<br /><br /> no (*x*-indefinido, *y*-0) y *z* - NaN|NaN|
|Error de intervalo de desbordamiento|HUGE_VAL, HUGE_VALF o HUGE_VALL|
|Error de intervalo de subdesbordamiento|valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Observaciones

Dado que C++ permite la sobrecarga, puede llamar a sobrecargas de **fma** que toman y devuelven **tipos float** y **long** **double.** En un programa C, **fma** siempre toma y devuelve un **doble**.

Esta función calcula el valor como si fuera de precisión infinita y luego redondea el resultado final.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
