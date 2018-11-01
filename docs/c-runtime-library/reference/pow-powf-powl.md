---
title: pow, powf, powl
ms.date: 04/05/2018
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: edf6116413caba52f9311f03bdfcc1d87e68a011
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452025"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Calcula *x* elevado a la potencia de *y*.

## <a name="syntax"></a>Sintaxis

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Base.

*y*<br/>
Exponente.

## <a name="return-value"></a>Valor devuelto

Devuelve el valor de *x*<sup>*y*</sup>. No se imprime ningún mensaje de error en caso de desbordamiento o subdesbordamiento.

|Valores de x e y|Valor devuelto de pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 y *y* == 0.0|1|
|*x* == 0.0 y *y* == 0.0|1|
|*x* == 0.0 y *y* < 0|INF|

## <a name="remarks"></a>Comentarios

**Pow** no reconoce los valores de punto flotante enteros mayores que 2<sup>64</sup> (por ejemplo, 1.0E100).

**Pow** tiene una implementación que usa Extensiones SIMD de transmisión por secuencias 2 (SSE2). Para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2, consulte [_set_SSE2_enable](set-sse2-enable.md).

Dado que C++ admite sobrecargas, puede llamar a cualquiera de las distintas sobrecargas de **pow**. En un programa C, **pow** siempre toma dos **doble** valores y devuelve un **doble** valor.

La sobrecarga de `pow(int, int)` ya no está disponible. Si utiliza esta sobrecarga, el compilador puede emitir [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Para evitar este problema, convierta el primer parámetro **doble**, **float**, o **largo** **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-|-|-|
|**Pow**, **powf**, **powl**|\<math.h>|\<math.h> o \<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
