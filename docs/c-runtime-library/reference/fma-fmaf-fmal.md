---
title: fma, fmaf, fmal
ms.date: 04/05/2018
api_name:
- fma
- fmaf
- fmal
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
ms.openlocfilehash: 4ddc4061e5a24ee3b5176aedc569d134d85e0002
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957108"
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

*y*<br/>
Segundo valor que se va a multiplicar.

*z*<br/>
El valor que se va a agregar.

## <a name="return-value"></a>Valor devuelto

Devuelve `(x * y) + z`. El valor devuelto se redondea después con el formato de redondeo actual.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = Infinity, *y* = 0 o<br /><br /> *x* = 0, *y* = infinito|NaN|
|*x* o *y* = Exact ± Infinity, *z* = Infinity con el signo opuesto|NaN|
|*x* o *y* = Nan|NaN|
|not (*x* = 0, *y*= indefinido) y *z* = Nan<br /><br /> not (*x*= indefinido, *y*= 0) y *z* = Nan|NaN|
|Error de intervalo de desbordamiento|± HUGE_VAL, ± HUGE_VALF o ± HUGE_VALL|
|Error de intervalo de subdesbordamiento|valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **FMA** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **FMA** siempre toma y devuelve un **valor Double**.

Esta función calcula el valor como si fuera de precisión infinita y luego redondea el resultado final.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
