---
title: ctan, ctanf, ctanl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ctan
- ctanf
- ctanl
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
- ctan
- ctanf
- ctanl
- complex/ctan
- complex/ctanf
- complex/ctanl
dev_langs:
- C++
helpviewer_keywords:
- ctan function
- ctanf function
- ctanl function
ms.assetid: d3cbd25c-1e93-4a6d-8154-da42921f7223
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d12e438a635b768869cf39c1f86a92c01904a568
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="ctan-ctanf-ctanl"></a>ctan, ctanf, ctanl

Recupera la tangente de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex ctan(
   _Dcomplex z
);
_Fcomplex ctan(
   _Fcomplex z
);  // C++ only
_Lcomplex ctan(
   _Lcomplex z
);  // C++ only
_Fcomplex ctanf(
   _Fcomplex z
);
_Lcomplex ctanl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo que representa el ángulo en radianes.

## <a name="return-value"></a>Valor devuelto

La tangente de *z*.

|Entrada|Excepción SEH|**_matherr** (excepción)|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|ninguna|_DOMAIN|
|± ∞ (**tan**, **tanf**)|INVALID|_DOMAIN|

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **ctan** que toman y devuelven **_Fcomplex** y **_Lcomplex** valores. En un programa C, **ctan** siempre toma y devuelve un **_Dcomplex** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**Ctan**, **ctanf**, **ctanl**|\<complex.h>|\<ccomplex>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
