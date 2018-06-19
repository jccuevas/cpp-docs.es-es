---
title: asinh, asinhf, asinhl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
dev_langs:
- C++
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1387e44b885d0f1ed58113b87d26ba5928768c18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393295"
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

Calcula el seno hiperbólico inverso.

## <a name="syntax"></a>Sintaxis

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

El **asinh** funciones devuelven el seno hiperbólico inverso (arcoseno hiperbólico) de *x*. Esta función es válida en el dominio de punto flotante. Si *x* es un NaN reservado, indefinido o infinito, se devuelve el mismo valor.

|Entrada|Excepción SEH|**_matherr** (excepción)|
|-----------|-------------------|--------------------------|
|± QNAN, IND, INF|ninguna|ninguna|

## <a name="remarks"></a>Comentarios

Cuando usas C++, puede llamar a sobrecargas de **asinh** que toman y devuelven **float** o **largo** **doble** valores. En un programa C, **asinh** siempre toma y devuelve **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C necesario|Encabezado C++ necesario|
|--------------|--------------|------------------|
|**Asinh**, **asinhf**, **asinhl**|\<math.h>|\<cmath > o \<math.h <|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
