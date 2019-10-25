---
title: norm, normf, norml
ms.date: 04/05/2018
api_name:
- norm
- normf
- norml
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
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
ms.openlocfilehash: 8deaa07d984a3840c73e594535ffffc9078d4716
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951319"
---
# <a name="norm-normf-norml"></a>norm, normf, norml

Recupera la magnitud cuadrada de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parámetros

*z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

La magnitud cuadrada de *z*.

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de la **norma** que toman los valores **_Fcomplex** o **_Lcomplex** y devolver valores de tipo **float** o **Long Double** . En un programa de C, **Norm** siempre toma un valor **_Dcomplex** y devuelve un valor **Double** .

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**norm**, **normf**, **norml**|\<complex.h>|\<complex.h>|

Los tipos **_Fcomplex**, **_Dcomplex**y **_Lcomplex** son equivalentes específicos de Microsoft de los tipos C99 nativos no implementados **float _Complex**, **Double _Complex**y **Long Double _Complex**, respectivamente.  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
