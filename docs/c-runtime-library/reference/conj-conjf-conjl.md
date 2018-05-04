---
title: conj, conjf, conjl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- conj
- conjf
- conjl
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
- conj
- conjf
- conjl
- complex/conj
- complex/conjf
- complex/conjl
dev_langs:
- C++
helpviewer_keywords:
- conj function
- conjf function
- conjl function
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb91b566c499ba9f34c7c67c9cdc24d67924601d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="conj-conjf-conjl"></a>conj, conjf, conjl

Devuelve el conjugado complejo de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex conj(
   _Dcomplex z
);
_Fcomplex conj(
   _Fcomplex z
);  // C++ only
_Lcomplex conj(
   _Lcomplex z
);  // C++ only
_Fcomplex conjf(
   _Fcomplex z
);
_Lcomplex conjl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*Z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

El conjugado complejo de *z*.  El resultado tiene el mismo elemento real e imaginario como *z*, pero con signo opuesto.

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **conj** que toman y devuelven **_Fcomplex** y **_Lcomplex** valores. En un programa C, **conj** siempre toma y devuelve un **_Dcomplex** valor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**Conj**, **conjf**, **conjl**|\<complex.h>|\<ccomplex>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
