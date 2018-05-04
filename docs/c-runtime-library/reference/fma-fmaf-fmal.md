---
title: fma, fmaf, fmal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b28009a9c3cc4edceb9032660a0c2a71916dfb2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

*Z*<br/>
El valor que se va a agregar.

## <a name="return-value"></a>Valor devuelto

Devuelve `(x * y) + z`. El valor devuelto se redondea después con el formato de redondeo actual.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = infinito, *y* = 0 o<br /><br /> *x* = 0, *y* = infinito|NaN|
|*x* o *y* = ± exacta infinito, *z* = infinito con el signo opuesto|NaN|
|*x* o *y* = NaN|NaN|
|no (*x* = 0, *y*= indefinida) y *z* = NaN<br /><br /> no (*x*= indefinida, *y*= 0) y *z* = NaN|NaN|
|Error de intervalo de desbordamiento|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|
|Error de intervalo de subdesbordamiento|valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **fma** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **fma** siempre toma y devuelve un **doble**.

Esta función calcula el valor como si fuera de precisión infinita y luego redondea el resultado final.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
