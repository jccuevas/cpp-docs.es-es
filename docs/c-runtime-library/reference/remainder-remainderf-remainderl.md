---
title: remainder, remainderf, remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 6b2a1a94fa39f9e9474f7bc3da3150bf4134d35f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917849"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Calcula el resto del cociente de dos valores de punto flotante, redondeado al valor entero más cercano.

## <a name="syntax"></a>Sintaxis

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Numerador.

*sí*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

El resto de punto flotante de *x* / *y*. Si el valor de *y* es 0,0, **resto** devuelve un Nan silencioso. Para obtener información sobre la representación de un NaN silencioso por la familia **printf** , vea [printf, _printf_l, wprintf _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Observaciones

Las funciones de **resto** calculan el resto de punto flotante de *x* / *y* como *x* = x*n* \* *y* + *r*, donde *n*es el entero más *cercano de valor* a *x* / *y* y *n*es incluso cuando &#124; *n* - *x* / *y* &#124; = 1/2. Cuando *r* = 0, *r* tiene el mismo signo que *x*.

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **resto** que toman y devuelven valores de tipo **float** o **Long** **Double** . En un programa de C, **resto** siempre toma dos argumentos **dobles** y devuelve un **valor Double**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------|-|
|**resto**, **remainderf (**, **resto**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
