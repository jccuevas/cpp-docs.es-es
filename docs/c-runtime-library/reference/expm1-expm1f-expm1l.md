---
title: expm1, expm1f, expm1l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
dev_langs:
- C++
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba382fb29b5ec841d9acd127ad5f48e0ca7b68fa
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Calcula el valor exponencial en base e de un valor, menos uno.

## <a name="syntax"></a>Sintaxis

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor exponencial del punto flotante.

## <a name="return-value"></a>Valor devuelto

El **expm1** funciones devuelven un valor de punto flotante que representa e<sup>x</sup> - 1, si se realiza correctamente. Si se produce desbordamiento, **expm1** devuelve **HUGE_VAL**, **expm1f** devuelve **HUGE_VALF**, **expm1l** devuelve **HUGE_VALL**, y **errno** está establecido en **ERANGE**. Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **expm1** que toman y devuelven **float** y **largo** **doble** valores. En un programa C, **expm1** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**expm1**, **expm1f**, **expm1l**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
