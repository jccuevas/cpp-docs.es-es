---
title: remainder, remainderf, remainderl
ms.date: 04/05/2018
api_name:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 851f022325bb617cb2b0ae9a331b680b9d9fd303
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949424"
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

*y*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

El resto de punto flotante de *x* / *y*. Si el valor de *y* es 0,0, **resto** devuelve un Nan silencioso. Para obtener información sobre la representación de un NaN silencioso por la familia **printf** , vea [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Comentarios

Las funciones de **resto** calculan el resto de punto *flotante de* *x* / *y* como *x* = *n* \* *y* + *r*, donde *n* es el entero más cercano de valor a *x* / *y* y *n*es incluso cuando &#124; *n* - *x* / *y* &#124; = 1/2. Cuando *r* = 0, *r* tiene el mismo signo que *x*.

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **resto** que toman y devuelven valores de tipo **float** o **Long** **Double** . En un programa de C, **resto** siempre toma dos argumentos **dobles** y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------|-|
|**remainder**, **remainderf**, **remainderl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
