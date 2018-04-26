---
title: tgamma, tgammaf, tgammal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs:
- C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 951e5635ae1e2b8ee22af7cb26902bd309d62b40
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

Si se realiza correctamente, devuelve el valor gamma de *x*.

Puede producirse un error de intervalo si la magnitud de *x* es demasiado grande o demasiado pequeño para el tipo de datos. Puede producirse un error de dominio o intervalo si *x* < = 0.

|Problema|Volver|
|-----------|------------|
|x = ± 0|±INFINITY|
|x = entero negativo|NaN|
|x = - infinito|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|error de dominio|NaN|
|error de polo|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|
|error de intervalo de desbordamiento|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|
|error de intervalo de subdesbordamiento|el valor correcto después del redondeo.|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **tgamma** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **tgamma** siempre toma y devuelve un **doble**.

Si x es un número natural, esta función devuelve el factorial de (x-1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
