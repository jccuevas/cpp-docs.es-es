---
title: csinh, csinhf, csinhl | Microsoft Docs
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
- csinh
- csinhf
- csinhl
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
- csinh
- csinhf
- csinhl
- complex/csinh
- complex/csinhf
- complex/csinhl
dev_langs:
- C++
helpviewer_keywords:
- csinh function
- csinhf function
- csinhl function
ms.assetid: cc616e55-d14d-4cd3-91f0-fbee03ce5edf
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24d89a6ebe9dec9677ce68e78bedf02fac7292bb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="csinh-csinhf-csinhl"></a>csinh, csinhf, csinhl

Recupera el seno hiperbólico de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex csinh(
   _Dcomplex z
);
_Fcomplex csinh(
   _Fcomplex z
);  // C++ only
_Lcomplex csinh(
   _Lcomplex z
);  // C++ only
_Fcomplex csinhf(
   _Fcomplex z
);
_Lcomplex csinhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo que representa un ángulo en radianes.

## <a name="return-value"></a>Valor devuelto

El seno hiperbólico de *z*, en radianes.

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **csinh** que toman y devuelven **_Fcomplex** y **_Lcomplex** valores. En un programa C, **csinh** siempre toma y devuelve un **_Dcomplex** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**csinh**, **csinhf**, **csinhl**|\<complex.h>|\<ccomplex>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
