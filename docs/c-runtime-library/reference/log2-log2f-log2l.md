---
title: log2, log2f, log2l | Microsoft Docs
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
- log2
- log2l
- log2f
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
dev_langs:
- C++
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ddde058c61bfbe83013111e3376a84bd463cd650
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Determina el logaritmo binario (base 2) del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);

```

### <a name="parameters"></a>Parámetros

*x*<br/>
El valor del que se determina el logaritmo de base 2.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve el retorno log2 *x*.

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|error de dominio|NaN|
|error de polo|-HUGE_VAL, -HUGE_VALF o -HUGE_VALL|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Si x es un entero, esta función básicamente devuelve el índice de base cero del bit más significativo 1 de *x*.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**LOG2**, **log2f**, **log2l**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
