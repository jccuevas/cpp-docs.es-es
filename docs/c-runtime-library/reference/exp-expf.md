---
title: exp, expf, expl
ms.date: 4/2/2020
api_name:
- expf
- expl
- exp
- _o_exp
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: b6d4906212073ab8cb04a0ab77d1234d444a4c95
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909651"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Calcula el valor exponencial.

## <a name="syntax"></a>Sintaxis

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante en el que se va a exponentiate *la base logarítmica* natural.

## <a name="return-value"></a>Valor devuelto

Las funciones **exp** devuelven el valor exponencial del parámetro de punto flotante, *x*, si es correcto. Es decir, el resultado es *e*<sup>*x*</sup>, donde *e* es la base del logaritmo natural. En el desbordamiento, la función devuelve el INF (infinito) y, en el subdesbordamiento, **exp** devuelve 0.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± NaN no interactivo, indeterminado|None|_DOMAIN|
|± Infinito|INVALID|_DOMAIN|
|x ≥ 7,097827e+002|INEXACTO+DESBORDAMIENTO|OVERFLOW|
|X ≤ -7,083964e+002|INEXACTO+SUBDESBORDAMIENTO|DESBORDAMIENTO|

La función **exp** tiene una implementación que usa las extensiones SIMD de transmisión por secuencias 2 (sse2). Vea [_set_SSE2_enable](set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.

## <a name="remarks"></a>Observaciones

C++ permite las sobrecargas, por lo que puede llamar a las sobrecargas de **exp** que toman un argumento de tipo **float** o **Long Double** . En un programa de C, **exp** siempre toma y devuelve un **valor Double**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C necesario|Encabezado C++ necesario|
|--------------|---------------------|---|
|**exp**, **EXPF (**, **sol**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
