---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347922"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Calcula la función de error o la función de error complementaria de un valor.

## <a name="syntax"></a>Sintaxis

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

Las funciones **erf** devuelven la función de error Gauss de *x*. Las funciones **erfc** devuelven la función de error Gauss complementaria de *x*.

## <a name="remarks"></a>Observaciones

Las funciones **erf** calculan la función de error Gauss de *x*, que se define como:

![Función de error de x](media/crt_erf_formula.PNG "Función de error de x")

La función de error Gauss complementaria se define como 1 - erf(x). Las funciones **erf** devuelven un valor en el intervalo -1.0 a 1.0. No se devuelve ningún error. Las funciones **erfc** devuelven un valor en el intervalo de 0 a 2. Si *x* es demasiado grande para **erfc**, la variable **errno** se establece en **ERANGE**.

Dado que C++ permite la sobrecarga, puede llamar a sobrecargas de **erf** y **erfc** que toman y devuelven **tipos float** y **long** **double.** En un programa C, **erf** y **erfc** siempre toman y devuelven un **doble**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**erf**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
