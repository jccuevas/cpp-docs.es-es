---
title: trunc, truncf, truncl
ms.date: 04/05/2018
apiname:
- trunc
- truncf
- truncl
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
ms.openlocfilehash: 6e023b9d894ea1b40a0e056e73b7c32f1e3cbed7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519865"
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

Si se realiza correctamente, devuelve un valor entero de *x*redondeado a cero.

De lo contrario, es posible que devuelva uno de los siguientes:

|Problema|Volver|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* = ± 0|x|
|*x* = NaN|NaN|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **trunc** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **trunc** siempre toma y devuelve un **doble**.

Dado que los valores de punto flotante más grandes son enteros exactos, esta función no se desborda por sí misma. Pero puede hacer que la función se desborde al devolver un valor en un tipo entero.

También se puede redondear a la baja mediante la conversión implícita de punto flotante a entero, aunque esta operación se limita a los valores que pueden almacenarse en el tipo de destino.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**TRUNC**, **truncf**, **truncl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
