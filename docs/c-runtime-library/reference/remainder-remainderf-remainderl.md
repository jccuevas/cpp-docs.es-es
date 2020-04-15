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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4b70d3175a125d72ff67710c83899c44dbf72015
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332867"
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

*X*<br/>
Numerador.

*y y*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

El resto de punto flotante de *x* / *y*. Si el valor de *y* es 0.0, **el resto** devuelve un NaN silencioso. Para obtener información sobre la representación de un NaN silencioso por la familia **printf,** véase [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Observaciones

Las funciones **de resto** calculan el resto de punto flotante *r* de *x* / *y* de modo que *x* = *n* \* *y* + *r*, donde *n*es el entero más cercano en valor a *x* / *y* y *n*es incluso siempre que &#124; *n* - *x* / *y* &#124; a 1/2. Cuando *r* es 0, *r* tiene el mismo signo que *x*.

Dado que C++ permite la sobrecarga, puede llamar a sobrecargas de **resto** que toman y devuelven **valores float** o **long** **double.** En un programa C, **el resto** siempre toma dos argumentos **dobles** y devuelve un **valor doble**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------|-|
|**resto,** **resto,** **resto**|\<math.h>|\<cmath> o \<math.h>|

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
