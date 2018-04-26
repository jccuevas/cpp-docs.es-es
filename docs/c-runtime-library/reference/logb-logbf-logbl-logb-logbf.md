---
title: logb, logbf, logbl, _logb, _logbf | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
dev_langs:
- C++
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f279d2b31ba9a40dd3d5c0e5d3c50e5a9a4b170
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf

Extrae el valor de exponente de un argumento de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

**logb** devuelve el valor de exponente imparcial de *x* como un entero con signo representado como un valor de punto flotante.

## <a name="remarks"></a>Comentarios

El **logb** funciones extraen el valor exponencial del argumento de punto flotante *x*, como si *x* se representara con el intervalo infinito. Si el argumento *x* es desnormalizado, se trata como si fuera normalizado.

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **logb** que toman y devuelven **float** o **largo** **doble** valores. En un programa C, **logb** siempre toma y devuelve un **doble**.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|Ninguna|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb**, **logbf**, **logbl**, **_logbf**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
