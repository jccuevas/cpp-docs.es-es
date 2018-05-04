---
title: frexp, frexpf, frexpl | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- frexp
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
- frexp
- _frexpl
dev_langs:
- C++
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bf79e954274b1cedb104ed637ad14b8e1c6431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

*x*<br/>
Valor de punto flotante.

*expptr*<br/>
Puntero al exponente de entero almacenado.

## <a name="return-value"></a>Valor devuelto

**frexp** devuelve la mantisa. Si *x* es 0, la función devuelve 0 para la mantisa y el exponente. Si *expptr* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve 0.

## <a name="remarks"></a>Comentarios

El **frexp** función desglosa el valor de punto flotante (*x*) en una mantisa (*m*) y un exponente (*n*), tal que absoluto valor de *m* es mayor o igual a 0,5 y menor que 1,0, y *x* = *m* * 2<sup>*n*</sup>. El exponente de entero *n* se almacena en la ubicación señalada por *expptr*.

C++ permite las sobrecargas, es posible llamar a las sobrecargas de **frexp**. En un programa C, **frexp** siempre tiene un **doble** y **int** puntero y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
