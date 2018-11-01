---
title: fmin, fminf, fminl
ms.date: 04/05/2018
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
ms.openlocfilehash: f73853e18bd5d7f699cd2c3109fe5fb830859bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464368"
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

Si es correcto, devuelve el menor de *x* o *y*.

|Entrada|Resultado|
|-----------|------------|
|*x* es NaN|*y*|
|*y* es NaN|*x*|
|*x* y *y* son NaN|NaN|

No hace que la función [_matherr](matherr.md) que se invoque, producir las excepciones de punto flotante o cambie el valor de **errno**.

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **fmin** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **fmin** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Fmin**, **fminf**, **fminl**|C: \<math.h><br />C++: \<math.h> o \<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
