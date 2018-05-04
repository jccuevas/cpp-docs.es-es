---
title: _Cmulcc, _FCmulcc, _LCmulcc | Documentos de Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1c4290c7e1f7a1ec917f2b2a197f787d28b9cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

Multiplica dos números complejos.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Uno de los operandos complejos para multiplicar.

*y*<br/>
El otro operando complejo para multiplicar.

## <a name="return-value"></a>Valor devuelto

A **_Dcomplex**, **_Fcomplex**, o **_Lcomplex** estructura que representa el producto complejo de los números complejos *x* y *y*.

## <a name="remarks"></a>Comentarios

Dado que los operadores aritméticos integrados no funcionan en la implementación de Microsoft de los tipos complejos, el **_Cmulcc**, **_FCmulcc**, y **_LCmulcc** funciones simplificar la multiplicación de tipos complejos.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**_Cmulcc**, **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

Estas funciones son específicos de Microsoft. Los tipos de **_Dcomplex**, **_Fcomplex**, y **_Lcomplex** son equivalentes específicos de Microsoft para los tipos nativos no implementados de C99 **_Complex dobles** , **float _Complex**, y **_Complex long double**, respectivamente. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
