---
title: fdim, fdimf, fdiml | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdcad02c94717715fdda1b3a9d2e820fc16d0bf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Determina la diferencia positiva entre el primer y el segundo valor.

## <a name="syntax"></a>Sintaxis

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Parámetros

*x*<br/>
Primer valor.

*y*<br/>
Segundo valor.

## <a name="return-value"></a>Valor devuelto

Devuelve la diferencia positiva entre *x* y *y*:

|Valor devuelto|Escenario|
|------------------|--------------|
|x-y|si x > y|
|0|si x <= y|

De lo contrario, puede que devuelva uno de los siguientes errores:

|Problema|Volver|
|-----------|------------|
|Error de intervalo de desbordamiento|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|
|Error de intervalo de subdesbordamiento|valor correcto (después del redondeo)|
|*x* o *y* es NaN|NaN|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **fdim** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **fdim** siempre toma y devuelve un **doble**.

Excepto para el control de NaN, esta función es equivalente a `fmax(x - y, 0)`.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fdim**, **fdimf**, **fdiml**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
