---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: b137fd131536da6b8630b9cadf69238ce48964bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909334"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Devuelve el siguiente valor de punto flotante que se pueda representar.

## <a name="syntax"></a>Sintaxis

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante del que se va a comenzar.

*sí*<br/>
Valor de punto flotante al que se va.

## <a name="return-value"></a>Valor devuelto

Devuelve el siguiente valor de punto flotante que se va a representar del tipo de valor devuelto después de *x* en la dirección de *y*. Si *x* e *y* son iguales, la función devuelve *y*, convertido al tipo de valor devuelto, sin ninguna excepción desencadenada. Si *x* no es *igual a y y el*resultado es un valor desnormalizado o cero, se establecen los Estados de excepción de punto flotante **FE_UNDERFLOW** y **FE_INEXACT** , y se devuelve el resultado correcto. Si *x* o *y* es un Nan, el valor devuelto es uno de los Nan de entrada. Si *x* es finito y el resultado es infinito o no representable en el tipo, se devuelve un infinito o Nan firmado correctamente, se establecen los Estados de excepción de punto flotante **FE_OVERFLOW** y **FE_INEXACT** , y **errno** se establece en **ERANGE**.

## <a name="remarks"></a>Observaciones

Las familias de funciones **nextafter** y **nexttoward** son equivalentes, excepto el tipo de parámetro de *y*. Si *x* e *y son iguales* , el valor devuelto es *y* se convierte en el tipo de valor devuelto.

Dado que C++ permite las sobrecargas, si \<incluye CMATH> puede llamar a las sobrecargas de **nextafter** y **nexttoward** que devuelven los tipos **float** y **Long** **Double** . En un programa de C, **nextafter** y **nexttoward** siempre devuelven el valor **Double**.

Las funciones **_nextafter** y **_nextafterf** son específicas de Microsoft. La función **_nextafterf** solo está disponible cuando se compila para x64.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<math.h>|\<math.h> o \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
