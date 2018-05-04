---
title: nearbyint, nearbyintf, nearbyintl | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2362a68bf73a370f2fdf8eaa5ecb18b0a08bfaad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

Si se realiza correctamente, devuelve *x*, redondeado al entero más próximo, usando el formato de redondeo actual devuelto por [fegetround](fegetround-fesetround2.md). De lo contrario, es posible que la función devuelva uno de los siguientes valores:

|Problema|Volver|
|-----------|------------|
|*x* = ±INFINITY|±Infinity, sin cambios|
|*x* = ± 0|± 0, sin cambios|
|*x* = NaN|NaN|

No se notifican errores a través de [_matherr](matherr.md); en concreto, esta función no informa de cualquier **FE_INEXACT** excepciones.

## <a name="remarks"></a>Comentarios

La principal diferencia entre esta función y [rint](rint-rintf-rintl.md) es que esta función no provoca la excepción de punto flotante inexacto.

Dado que los valores de punto flotante máximos son enteros exactos, esta función nunca se desbordará por sí misma, sino que la salida podría desbordar el valor devuelto, según la versión de la función que use.

C++ permite las sobrecargas, es posible llamar a las sobrecargas de **nearbyint** que toman y devuelven **float** o **largo** **doble** parámetros. En un programa C, **nearbyint** siempre toma dos valores double y devuelve un valor de tipo double.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[Matemáticas y compatibilidad de punto flotante](../floating-point-support.md)<br/>
