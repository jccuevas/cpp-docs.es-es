---
title: cacos, cacosf, cacosl | Microsoft Docs
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
- cacos
- cacosf
- cacosl
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
- cacos
- cacosf
- cacosl
- complex/cacos
- complex/cacosf
- complex/cacosl
dev_langs:
- C++
helpviewer_keywords:
- cacos function
- cacosf function
- cacosl function
ms.assetid: 78118c00-0a07-49c1-8a13-4bf19ce3aea8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a15f2487b95375d0f6f83026c5cd2dc37402600b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="cacos-cacosf-cacosl"></a>cacos, cacosf, cacosl

Recupera el arco coseno de un número complejo, con cortes de bifurcación fuera del intervalo [-1, + 1] en el eje real.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex cacos( _Dcomplex z );
_Fcomplex cacosf( _Fcomplex z );
_Lcomplex cacosl( _Lcomplex z );
```

```cpp
_Fcomplex cacos( _Fcomplex z );  // C++ only
_Lcomplex cacos( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo que representa un ángulo en radianes.

## <a name="return-value"></a>Valor devuelto

El arco coseno de *z*, en radianes. El resultado es ilimitado a lo largo del eje imaginario y en el en el intervalo [0, π] en el eje real. Se producirá un error de dominio si *z* está fuera del intervalo [-1, + 1].

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **cacos** que toman y devuelven **_Fcomplex** y **_Lcomplex** valores. En un programa C, **cacos** siempre toma y devuelve un **_Dcomplex** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**cacos**, **cacosf**, **cacosl**|\<complex.h>|\<ccomplex>|

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
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
