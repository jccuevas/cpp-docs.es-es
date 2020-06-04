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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: def04602cdeb0ad180bd4c51c02f570c94809784
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914636"
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

*x*<br/>
Valor de punto flotante.

*IntPtr*<br/>
Puntero a la parte entera almacenada.

## <a name="return-value"></a>Valor devuelto

Esta función devuelve la parte fraccionaria con signo de *x*. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

Las funciones **MODF (** dividen el valor de punto flotante *x* en partes fraccionarias y enteros, cada uno de los cuales tiene el mismo signo que *x*. Se devuelve la parte fraccionaria con signo de *x* . La parte entera se almacena como un valor de punto flotante en *IntPtr*.

**MODF (** tiene una implementación que usa las extensiones SIMD de streaming 2 (sse2). Vea [_set_SSE2_enable](set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.

C++ permite las sobrecargas, por lo que puede llamar a las sobrecargas de **MODF (** que toman y devuelven parámetros de tipo **float** o **Long** **Double** . En un programa de C, **MODF (** siempre toma dos valores double y devuelve un valor Double.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**MODF (**, **modff (**, **modfl**|C: \<math.h><br /><br /> C++: \<cmath> o \<math.h>|

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
