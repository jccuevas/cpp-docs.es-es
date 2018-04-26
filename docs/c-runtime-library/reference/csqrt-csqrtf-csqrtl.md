---
title: csqrt, csqrtf, csqrtl | Microsoft Docs
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
- csqrt
- csqrtf
- csqrtl
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
- csqrt
- csqrtf
- csqrtl
- complex/csqrt
- complex/csqrtf
- complex/csqrtl
dev_langs:
- C++
helpviewer_keywords:
- csqrt function
- csqrtf function
- csqrtl function
ms.assetid: b65f086b-0f55-4622-a7a3-4e79d9c9c05c
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad6424497abc6f45eaf8369aabca4ad966881f4c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="csqrt-csqrtf-csqrtl"></a>csqrt, csqrtf, csqrtl

Recupera la raíz cuadrada de un número complejo, con un corte de bifurcación en el eje negativo real.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex csqrt(
   _Dcomplex z
);
_Fcomplex csqrt(
   _Fcomplex z
);  // C++ only
_Lcomplex csqrt(
   _Lcomplex z
);  // C++ only
_Fcomplex csqrtf(
   _Fcomplex z
);
_Lcomplex csqrtl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

La raíz cuadrada de *z*. El resultado se encuentra en el semiplano derecho.

|Entrada|Excepción SEH|**_matherr** (excepción)|
|-----------|-------------------|--------------------------|
|± QNAN, IND|ninguna|_DOMAIN|
|- ∞|ninguna|_DOMAIN|

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **csqrt** que toman y devuelven **_Fcomplex** y **_Lcomplex** valores. En un programa C, **csqrt** siempre toma y devuelve un **_Dcomplex** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**csqrt**, **csqrtf**, **csqrtl**|\<complex.h>|\<ccomplex>|

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
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
