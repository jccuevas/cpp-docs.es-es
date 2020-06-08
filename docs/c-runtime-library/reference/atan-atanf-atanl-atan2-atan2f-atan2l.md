---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 6/5/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 41007e08884da6ccac09c7dc98cef12381e4b45a
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506785"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Calcula el arco tangente de **x** (**atan**, **atanf (** y **atanl**) o el arco tangente de **y** / **x** (**ATAN2**, **atan2f (** y **atan2l**).

## <a name="syntax"></a>Sintaxis

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Cualquier número.

## <a name="return-value"></a>Valor devuelto

**atan** devuelve el arco tangente de *x* en el intervalo-π/2 a π/2 radianes. **ATAN2** devuelve el arco tangente de *y* / *x* en el intervalo-π a π radianes. Si *x* es 0, **atan** devuelve 0. Si ambos parámetros de **ATAN2** son 0, la función devuelve 0. Todos los resultados están en radianes.

**ATAN2** utiliza los signos de ambos parámetros para determinar el cuadrante del valor devuelto.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|ninguno|**_DOMAIN**|

## <a name="remarks"></a>Comentarios

La función **atan** calcula el arcotangente (la función tangente inversa) de *x*. **ATAN2** calcula el arco tangente de *y* / *x* (si *x* es igual a 0, **ATAN2** devuelve π/2 Si *y* es positivo,-π/2 Si *y* es negativo, o 0 si *y* es 0).

**atan** tiene una implementación que usa las extensiones SIMD de streaming 2 (sse2). Para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2, consulte [_set_SSE2_enable](set-sse2-enable.md).

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **atan** y **ATAN2** que toman argumentos de tipo **float** o **Long** **Double** . En un programa de C, **atan** y **ATAN2** siempre toman argumentos **dobles** y devuelven un valor **Double**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------|-|
|**atan**, **ATAN2**, **atanf (**, **atan2f (**, **atanl**, **atan2l**|\<math.h>|\<cmath> o \<math.h>|

## <a name="example"></a>Ejemplo

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>Vea también

[Compatibilidad de punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
