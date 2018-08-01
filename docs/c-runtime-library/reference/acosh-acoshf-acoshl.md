---
title: acosh, acoshf, acoshl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- acoshf
- acosh
- acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
dev_langs:
- C++
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546006fcf1c559317b4afff424976db8109442e7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404757"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Calcula el coseno hiperbólico inverso.

## <a name="syntax"></a>Sintaxis

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
```

```cpp
float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*  
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

El **acosh** funciones devuelven el coseno hiperbólico inverso (arco coseno hiperbólico) de *x*. Estas funciones son válidas en el dominio *x* ≥ 1. Si *x* es menor que 1, `errno` está establecido en `EDOM` y el resultado es un valor NaN. Si *x* es un NaN reservado, indefinido o infinito, se devuelve el mismo valor.

|Entrada|Excepción SEH|Excepción de`_matherr` |
|-----------|-------------------|--------------------------|
|± QNAN, IND, INF|ninguna|ninguna|
|*x* < 1|ninguna|ninguna|

## <a name="remarks"></a>Comentarios

Cuando usas C++, puede llamar a sobrecargas de **acosh** que toman y devuelven **float** o **largo** **doble** valores. En un programa C, **acosh** siempre toma y devuelve **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**ACOSH**, **acoshf**, **acoshl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_acosh.c
// Compile by using: cl /W4 crt_acosh.c
// This program displays the hyperbolic cosine of pi / 4
// and the arc hyperbolic cosine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = cosh( pi / 4 );
   y = acosh( x );
   printf( "cosh( %f ) = %f\n", pi/4, x );
   printf( "acosh( %f ) = %f\n", x, y );
}
```

```Output
cosh( 0.785398 ) = 1.324609
acosh( 1.324609 ) = 0.785398
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)  
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)  
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)  
[cosh, coshf, coshl](cosh-coshf-coshl.md)  
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)  
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)  