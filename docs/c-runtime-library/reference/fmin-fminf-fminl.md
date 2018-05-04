---
title: Fmin, fminf, fminl | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abf16c4cc21d1dc396f0b81aadc8d495c6bdd4b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Determina el menor de los dos valores especificados.

## <a name="syntax"></a>Sintaxis

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Primer valor que se va a comparar.

*y*<br/>
Segundo valor que se va a comparar.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve el menor de *x* o *y*.

|Entrada|Resultado|
|-----------|------------|
|*x* es NaN|*y*|
|*y* es NaN|*x*|
|*x* y *y* son NaN|NaN|

No hace que la función [_matherr](matherr.md) para invocar, hacer que las excepciones de punto flotante o cambie el valor de **errno**.

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **fmin** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **fmin** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Fmin**, **fminf**, **fminl**|C: \<math.h><br />C++: \<math.h> o \<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
