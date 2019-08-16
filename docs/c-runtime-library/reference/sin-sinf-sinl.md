---
title: sin, sinf, sinl
ms.date: 04/10/2018
apiname:
- sinl
- sinf
- sin
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
- _sinl
- sinf
- sinl
- sin
helpviewer_keywords:
- _sinl function
- sinl function
- calculating sines
- sin function
- trigonometric functions
- sinf function
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
ms.openlocfilehash: 7006d7246837e5dc69733a007b3f7dab1c55280e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356257"
---
# <a name="sin-sinf-sinl"></a>sin, sinf, sinl

Calcula el seno del valor de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double sin(double x);
float sinf(float x);
long double sinl(long double x);
```

```cpp
float sin(float x);  // C++ only
long double sin(long double x);  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Ángulo en radianes.

## <a name="return-value"></a>Valor devuelto

El **pecado** funciones devuelven el seno de *x*. Si *x* es mayor o igual que 263 o menor o igual que -263, se produce una pérdida de significado en el resultado.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|Ninguna|_DOMAIN|
|± ∞ (sin, sinf, sinl)|INVALID|_DOMAIN|

Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **pecado** que toman y devuelven **float** o **largo** **doble** valores. En un programa C, **pecado** siempre toma y devuelve **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-|-|-|
|**sin**, **sinf**, **sinl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_sincos.c
// This program displays the sine and cosine of pi / 2.
// Compile by using: cl /W4 crt_sincos.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sin( x );
   printf( "sin( %f ) = %f\n", x, y );
   y = cos( x );
   printf( "cos( %f ) = %f\n", x, y );
}
```

```Output
sin( 1.570796 ) = 1.000000
cos( 1.570796 ) = 0.000000
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIsin](../../c-runtime-library/cisin.md)<br/>
