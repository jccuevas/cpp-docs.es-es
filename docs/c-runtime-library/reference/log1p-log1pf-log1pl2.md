---
title: log1p, log1pf, log1pl2 | Microsoft Docs
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
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf512bcf898a202eee771318afb022642d432b4f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Calcula el logaritmo natural de 1 más el valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);

```

### <a name="parameters"></a>Parámetros

*x*<br/>
El argumento de punto flotante.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve natural (base -*e*) de registro del (*x* + 1).

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Entrada|Resultado|Excepción SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Desnormalizados|Igual que la entrada|UNDERFLOW||
|±0|Igual que la entrada|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|±SNaN|Igual que la entrada|INVALID||
|±QNaN, indefinida|Igual que la entrada|||

El **errno** valor se establece en ERANGE si *x* = -1. El **errno** valor se establece en **EDOM** si *x* < -1.

## <a name="remarks"></a>Comentarios

El **log1p** funciones pueden ser más precisas que el uso de `log(x + 1)` cuando *x* esté cerca de 0.

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **log1p** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **log1p** siempre toma y devuelve un **doble**.

Si *x* es un número natural, esta función devuelve el logaritmo del factorial de (*x* - 1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
