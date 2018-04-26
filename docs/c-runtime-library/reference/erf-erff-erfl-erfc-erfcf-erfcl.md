---
title: erf, erff, erfl, erfc, erfcf, erfcl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs:
- C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1703b4e352fee798a7b38dd16edf6158cd7f53ea
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

El **erf** funciones devuelven una función de error de la Gauss *x*. El **erfc** funciones devuelven el Gauss complementaria función de error de *x*.

## <a name="remarks"></a>Comentarios

El **erf** funciones calculan la función error de Gauss de *x*, que se define como:

![Función de error de x](media/crt_erf_formula.PNG "CRT_erf_formula")

La función error de Gauss complementaria se define como 1 - ERF. El **erf** funciones devuelven un valor en el intervalo de -1,0 y 1,0. No se devuelve ningún error. El **erfc** funciones devuelven un valor en el intervalo de 0 a 2. Si *x* es demasiado grande para **erfc**, **errno** variable se establece en **ERANGE**.

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **erf** y **erfc** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **erf** y **erfc** siempre toman y devuelven un **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**ERF**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
