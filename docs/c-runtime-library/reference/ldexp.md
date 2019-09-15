---
title: ldexp, ldexpf, ldexpl
ms.date: 04/05/2018
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 7fabd00c7ddc5c430c158089b7e5769158b46328
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953504"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp, ldexpf, ldexpl

Multiplica un número de punto flotante por una potencia integral de dos.

## <a name="syntax"></a>Sintaxis

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

*exp*<br/>
Exponente de entero.

## <a name="return-value"></a>Valor devuelto

Las funciones **ldexp** devuelven el valor de *x* \* 2<sup>*exp*</sup> si se realiza correctamente. En el desbordamiento, y en función del signo de *x*, **ldexp** devuelve +/- **HUGE_VAL**; el valor **errno** se establece en **ERANGE**.

Para obtener más información sobre **errno** y los posibles valores devueltos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **ldexp** que toman tipos **float** o **Long** **Double** . En un programa de C, **ldexp** siempre toma un **valor Double** y un **entero** y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**ldexp**, **ldexpf**, **ldexpl**|\<math.h>|\<cmath>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Resultados

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
