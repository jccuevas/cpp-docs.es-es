---
title: rint, rintf, rintl
ms.date: 04/05/2018
api_name:
- rintf
- rintl
- rint
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: ac9db3ee5a50bb334754a8a1191638a319829b97
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170896"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Redondea un valor de punto flotante al entero más cercano en el formato de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
```

```cpp
float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a redondear.

## <a name="return-value"></a>Valor devuelto

Las funciones **rimir** devuelven un valor de punto flotante que representa el entero más cercano a *x*. Los valores de la mitad se redondean de acuerdo con la configuración actual del modo de redondeo de punto flotante, igual que las funciones de **nearbyint (** . A diferencia de las funciones **nearbyint (** , las funciones **rimir** pueden generar la **FE_INEXACT** excepción de punto flotante si el resultado difiere en el valor del argumento. No se devuelve ningún error.

|Entrada|Excepción SEH|**_matherr** Excepcional|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|None|None|
|Desnormalizados|EXCEPTION_FLT_UNDERFLOW|None|

## <a name="remarks"></a>Observaciones

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **rimir** que toman y devuelven valores de tipo **float** y **Long** **Double** . En un programa de C, **rimir** siempre toma y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**rimir**, **rintf**, **rintl**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>
