---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
dev_langs:
- C++
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 678e135c3cb1e3c8d0064f21081e4b68a7eac329
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

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

*y*<br/>
Valor de punto flotante al que se va.

## <a name="return-value"></a>Valor devuelto

Devuelve el siguiente valor de punto flotante puede representar de tipo de valor devuelto después de *x* en la dirección de *y*. Si *x* y *y* son iguales, la función devuelve *y*, convertido en el tipo de valor devuelto con ninguna excepción activada. Si *x* no es igual a *y*, y el resultado es cero, o un desnormalizados el **FE_UNDERFLOW** y **FE_INEXACT** Estados de excepción de punto flotante se establecen, y se devuelve el resultado correcto. Si el valor *x* o *y* es un NAN, entonces el valor devuelto es uno de los valores de entrada NaN. Si *x* es finito y el resultado es infinito o no se puede representar en el tipo, se devuelve un signo correcto infinito ni NAN, la **FE_OVERFLOW** y **FE_INEXACT** se establecen los Estados de excepción de punto flotante, y **errno** está establecido en **ERANGE**.

## <a name="remarks"></a>Comentarios

El **nextafter** y **nexttoward** familias de función son equivalentes, salvo por el tipo de parámetro *y*. Si *x* y *y* son iguales, el valor devuelto es *y* convierte al tipo de valor devuelto.

Como C++ permite las sobrecargas, si incluye \<cmath > se pueden llamar a las sobrecargas de **nextafter** y **nexttoward** que devuelven **float** y **long** **doble** tipos. En un programa C, **nextafter** y **nexttoward** siempre devuelven **doble**.

El **_nextafter** y **_nextafterf** funciones son específicas de Microsoft. El **_nextafterf** función sólo está disponible cuando se compila para x64.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf** , **nexttowardl**|\<math.h>|\<math.h> o \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
