---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 4/2/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338585"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Redondea el valor de punto flotante especificado en un entero y devuelve ese valor con un formato de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parámetros

*X*<br/>
El valor que se va a redondear.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve *x*, redondeado al entero más cercano, utilizando el formato de redondeo actual según lo informado por [fegetround](fegetround-fesetround2.md). De lo contrario, es posible que la función devuelva uno de los siguientes valores:

|Problema|Valor devuelto|
|-----------|------------|
|*x* - -INFINITY|•INFINITY, sin modificar|
|*x* - 0|0, sin modificar|
|*x* - NaN|NaN|

Los errores no se notifican a través [de _matherr;](matherr.md) específicamente, esta función no notifica ninguna **excepción FE_INEXACT.**

## <a name="remarks"></a>Observaciones

La diferencia principal entre esta función y [rint](rint-rintf-rintl.md) es que esta función no genera la excepción de punto flotante inexacta.

Dado que los valores de punto flotante máximos son enteros exactos, esta función nunca se desbordará por sí misma, sino que la salida podría desbordar el valor devuelto, según la versión de la función que use.

C++ permite la sobrecarga, por lo que puede llamar a sobrecargas de **nearbyint** que toman y devuelven **float** o **long** **double** parámetros. En un programa C, **nearbyint** siempre toma dos valores dobles y devuelve un valor double.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[Compatibilidad con cálculos matemáticos y el punto flotante](../floating-point-support.md)<br/>
