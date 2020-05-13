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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d9e7adb321d85c728c5185c1663fd7f945fc4a82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914576"
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

*x*<br/>
El valor que se va a redondear.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve *x*, redondeado al entero más próximo, utilizando el formato de redondeo actual como indica el [fegetround](fegetround-fesetround2.md). De lo contrario, es posible que la función devuelva uno de los siguientes valores:

|Problema|Valor devuelto|
|-----------|------------|
|*x* = ± infinito|± INFINITO, sin modificar|
|*x* = ± 0|± 0, sin modificar|
|*x* = Nan|NaN|

Los errores no se registran a través de [_matherr](matherr.md); en concreto, esta función no notifica ninguna excepción **FE_INEXACT** .

## <a name="remarks"></a>Observaciones

La principal diferencia entre esta función y [rimir](rint-rintf-rintl.md) es que esta función no genera la excepción de punto flotante inexacto.

Dado que los valores de punto flotante máximos son enteros exactos, esta función nunca se desbordará por sí misma, sino que la salida podría desbordar el valor devuelto, según la versión de la función que use.

C++ permite las sobrecargas, por lo que puede llamar a las sobrecargas de **nearbyint (** que toman y devuelven parámetros de tipo **float** o **Long** **Double** . En un programa de C, **nearbyint (** siempre toma dos valores double y devuelve un valor Double.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**nearbyint (**, **nearbyintf (**, **nearbyintl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[Compatibilidad con cálculos matemáticos y el punto flotante](../floating-point-support.md)<br/>
