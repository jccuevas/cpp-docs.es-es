---
title: EXP, expf, expl | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- expf
- expl
- exp
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
- _expl
- expf
- expl
- exp
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9569eee475a80fc5c08c2ec1d099cf627c7b5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exp-expf-expl"></a>EXP, expf, expl

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
Valor del punto flotante a exponentiate la base del logaritmo natural *e* por.

## <a name="return-value"></a>Valor devuelto

El **exp** funciones devuelven el valor exponencial del parámetro de punto flotante, *x*, si se realiza correctamente. Es decir, el resultado es *e*<sup>*x*</sup>, donde *e* es la base del logaritmo natural. Si se produce desbordamiento, la función devuelve INF (infinito) y en subdesbordamiento, **exp** devuelve 0.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± Valor NaN reservado, indeterminado|Ninguna|_DOMAIN|
|± Infinito|INVALID|_DOMAIN|
|x ≥ 7,097827e+002|INEXACTO+DESBORDAMIENTO|OVERFLOW|
|X ≤ -7,083964e+002|INEXACTO+SUBDESBORDAMIENTO|DESBORDAMIENTO|

El **exp** función tiene una implementación que usa Extensiones SIMD de transmisión por secuencias 2 (SSE2). Consulte [_set_SSE2_enable](set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.

## <a name="remarks"></a>Comentarios

C++ permite las sobrecargas, es posible llamar a las sobrecargas de **exp** que toman un **float** o **long double** argumento. En un programa C, **exp** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C necesario|Encabezado C++ necesario|
|--------------|---------------------|---|
|**EXP**, **expf**, **expl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
