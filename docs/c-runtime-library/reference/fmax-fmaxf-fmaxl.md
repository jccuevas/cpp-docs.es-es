---
title: fmax, fmaxf, fmaxl | Microsoft Docs
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
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs:
- C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b108a01201e75d466f95f029f296c87c9b1430c7
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Determina el mayor de dos valores numéricos especificados.

## <a name="syntax"></a>Sintaxis

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
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

Si se realiza correctamente, devuelve el mayor de *x* o *y*. El valor devuelto es exacto y no depende de ninguna forma de redondeo.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* y *y* = NaN|NaN|

Esta función no usa los errores especificados en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a las sobrecargas de fmax que toman y devuelven los tipos float y long double. En un programa de C, fmax siempre toma y devuelve un tipo double.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**Fmax**, **fmaxf**, **fmaxl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
