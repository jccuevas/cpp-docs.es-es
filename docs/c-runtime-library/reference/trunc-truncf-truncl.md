---
title: trunc, truncf, truncl
ms.date: 04/05/2018
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: b0c615c91e562fa45f791d8cc20f39a830013aeb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946005"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Determina el entero más cercano menor o igual que el valor de punto flotante especificado.

## <a name="syntax"></a>Sintaxis

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor que se va a truncar.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve un valor entero de *x*, redondeado hacia cero.

De lo contrario, es posible que devuelva uno de los siguientes:

|Problema|Volver|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* =  ±0|x|
|*x* = Nan|NaN|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **trunc** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **trunc** siempre toma y devuelve un **valor Double**.

Dado que los valores de punto flotante más grandes son enteros exactos, esta función no se desborda por sí misma. Pero puede hacer que la función se desborde al devolver un valor en un tipo entero.

También se puede redondear a la baja mediante la conversión implícita de punto flotante a entero, aunque esta operación se limita a los valores que pueden almacenarse en el tipo de destino.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**trunc**, **truncf (** , **truncl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
