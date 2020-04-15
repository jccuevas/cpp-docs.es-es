---
title: frexp, frexpf, frexpl
ms.date: 4/2/2020
api_name:
- frexp
- _o_frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: 79fe70341f0d6fef1dc7fe00f872456a11972876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345794"
---
# <a name="frexp-frexpf-frexpl"></a>frexp, frexpf, frexpl

Obtiene la mantisa y el exponente de un número de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Valor de punto flotante.

*expptr*<br/>
Puntero al exponente de entero almacenado.

## <a name="return-value"></a>Valor devuelto

**frexp** devuelve la mantisa. Si *x* es 0, la función devuelve 0 tanto para la mantisa como para el exponente. Si *expptr* es **NULL**, se invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve 0.

## <a name="remarks"></a>Observaciones

La función **frexp** desglosa el valor de punto flotante (*x*) en una mantisa (*m*) y un exponente (*n*), de modo que el valor absoluto de *m* es mayor o igual que 0,5 y menor que 1,0, y *x* = *m* * 2<sup>*n*</sup>. El exponente entero *n* se almacena en la ubicación señalada por *expptr*.

C++ permite la sobrecarga, por lo que puede llamar a sobrecargas de **frexp**. En un programa C, **frexp** siempre toma un puntero **double** y un **int** y devuelve un **double**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
