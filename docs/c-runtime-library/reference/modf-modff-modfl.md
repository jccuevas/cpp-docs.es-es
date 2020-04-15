---
title: modf, modff, modfl
ms.date: 4/2/2020
api_name:
- modff
- modf
- modfl
- _o_modf
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: b509da5f18ea1f606b8a3b47ab66a78e4f595558
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338697"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

Divide un valor de punto flotante en partes fraccionarias y enteras.

## <a name="syntax"></a>Sintaxis

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Valor de punto flotante.

*Intptr*<br/>
Puntero a la parte entera almacenada.

## <a name="return-value"></a>Valor devuelto

Esta función devuelve la parte fraccionaria con signo de *x*. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

Las funciones **modf** desglosan el valor de punto flotante *x* en partes fraccionarias y enteras, cada una de las cuales tiene el mismo signo que *x*. Se devuelve la parte fraccionaria firmada de *x.* La parte entera se almacena como un valor de punto flotante en *intptr*.

**modf** tiene una implementación que utiliza Streaming SIMD Extensions 2 (SSE2). Vea [_set_SSE2_enable](set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.

C++ permite la sobrecarga, por lo que puede llamar a sobrecargas de **modf** que toman y devuelven **float** o **long** **double** parámetros. En un programa C, **modf** siempre toma dos valores dobles y devuelve un valor double.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**modf**, **modff**, **modfl**|C: \<math.h><br /><br /> C++: \<cmath> o \<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
