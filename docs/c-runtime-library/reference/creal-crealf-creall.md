---
title: creal, crealf, creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4dcdf60fee6d57b5561b72b477aa1a8bb31f35f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171221"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Recupera la parte real de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parámetros

*z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

La parte real de *z*.

## <a name="remarks"></a>Observaciones

Dado C++ que permite las sobrecargas, puede llamar a sobrecargas de **creal** que toman **_Fcomplex** o **_Lcomplex** valores, y devuelven valores de tipo **float** o **Long Double** . En un programa de C, **CREAL** siempre toma un valor **_Dcomplex** y devuelve un valor **Double** .

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**CREAL**, **crealf**, **creall**|\<complex.h>|\<ccomplex>|

Los tipos **_Fcomplex**, **_Dcomplex**y **_Lcomplex** son equivalentes específicos de Microsoft de los tipos de C99 nativo no implementados **float _Complex**, **Double _Complex**y **Long Double _Complex**, respectivamente. Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
