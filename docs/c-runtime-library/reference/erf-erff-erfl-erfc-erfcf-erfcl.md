---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 01/31/2019
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
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
ms.openlocfilehash: df724ed056c02d79b5b51f97ae4aaf8ae267fde5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "70937613"
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

*x*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

Las funciones **ERF** devuelven la función de error de Gauss de *x*. Las funciones **erfc** devuelven la función de error de Gauss complementaria de *x*.

## <a name="remarks"></a>Comentarios

Las funciones **ERF** calculan la función de error de Gauss de *x*, que se define como:

![La función de error de x](media/crt_erf_formula.PNG "Función de error de x")

La función de error de Gauss complementaria se define como 1-Fun (x). Las funciones **ERF** devuelven un valor en el intervalo de-1,0 a 1,0. No se devuelve ningún error. Las funciones **erfc** devuelven un valor en el intervalo comprendido entre 0 y 2. Si *x* es demasiado grande para **erfc**, la variable **errno** se establece en **ERANGE**.

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **Fun** y **erfc** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **Fun** y **erfc** siempre toman y devuelven un **valor Double**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**Fun**, **erff (** , **erfl**, **erfc**, **erfcf (** , **erfcl**|\<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
