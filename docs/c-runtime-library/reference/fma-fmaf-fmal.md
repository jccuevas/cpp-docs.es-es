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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: be3578aa9c66f329e191749b4506091bff69b1eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914948"
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

*x*<br/>
Primer valor que se va a multiplicar.

*sí*<br/>
Segundo valor que se va a multiplicar.

*z*<br/>
El valor que se va a agregar.

## <a name="return-value"></a>Valor devuelto

Devuelve `(x * y) + z`. El valor devuelto se redondea después con el formato de redondeo actual.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Valor devuelto|
|-----------|------------|
|*x* = Infinity, *y* = 0 o<br /><br /> *x* = 0, *y* = infinito|NaN|
|*x* o *y* = Exact ± Infinity, *z* = Infinity con el signo opuesto|NaN|
|*x* o *y* = Nan|NaN|
|not (*x* = 0, *y*= indefinido) y *z* = Nan<br /><br /> not (*x*= indefinido, *y*= 0) y *z* = Nan|NaN|
|Error de intervalo de desbordamiento|± HUGE_VAL, ± HUGE_VALF o ± HUGE_VALL|
|Error de intervalo de subdesbordamiento|valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Observaciones

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **FMA** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **FMA** siempre toma y devuelve un **valor Double**.

Esta función calcula el valor como si fuera de precisión infinita y luego redondea el resultado final.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf (**, **fmal**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
