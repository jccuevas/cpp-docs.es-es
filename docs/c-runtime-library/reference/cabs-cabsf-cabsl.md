---
title: cabs, cabsf, cabsl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- cabs
- cabsf
- cabsl
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
- cabs
- cabsf
- cabsl
- complex/cabs
- complex/cabsf
- complex/cabsl
dev_langs:
- C++
helpviewer_keywords:
- cabs function
- cabsf function
- cabsl function
ms.assetid: 6b8eb453-cc8f-4972-bebf-351cbdfdfc15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c14252e7857331482b0fe6f99dd56e49ab838dd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cabs-cabsf-cabsl"></a>cabs, cabsf, cabsl

Recupera el valor absoluto de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
double cabs(
   _Dcomplex z
);
float cabs(
   _Fcomplex z
);  // C++ only
long double cabs(
   _Lcomplex z
);  // C++ only
float cabsf(
   _Fcomplex z
);
long double cabsl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

El valor absoluto de *z*.

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **cabs** que toman **_Fcomplex** o **_Lcomplex** valores y devuelven **float** o **largo** **doble** valores. En un programa C, **cabs** siempre tiene un **_Dcomplex** valor determinado y devuelve un **doble** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**Cabs**, **cabsf**, **cabsl**|\<complex.h>|\<ccomplex>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
