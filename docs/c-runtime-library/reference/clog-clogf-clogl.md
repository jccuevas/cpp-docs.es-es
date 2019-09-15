---
title: clog, clogf, clogl
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 76ee6e4e81c275c8cbed0f74914521c0b44499bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942925"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Recupera el logaritmo natural de un número complejo, con un corte de bifurcación en el eje negativo real.

## <a name="syntax"></a>Sintaxis

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parámetros

*z*<br/>
Base del logaritmo.

## <a name="return-value"></a>Valor devuelto

Logaritmo natural de *z*. El resultado es ilimitado a lo largo del eje real y en el intervalo [-iπ, + iπ] a lo largo del eje imaginario.

Los valores de devolución posibles son:

|parámetro de z|Valor devuelto|
|-----------------|------------------|
|Positivo|Logaritmo en base 10 de z|
|Cero|- ∞|
|Negativo|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas del **obstruya** que toman y devuelven los valores de **_Fcomplex** y **_Lcomplex** . En un programa de C, el **obstruya** siempre toma y devuelve un valor de **_Dcomplex** .

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**clog**,               **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
