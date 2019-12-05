---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858027"
---
# <a name="_div64"></a>_div64

El intrínseco `_div64` divide un entero de 64 bits por un entero de 32 bits. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_div64` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parameters

*dividend* \
de Entero de 64 bits que se va a dividir.

 \ *divisor*
de Entero de 32 bits por el que se va a dividir.

*remainder* \
enuncia Los bits enteros de 32 bits del resto.

## <a name="return-value"></a>Valor devuelto

Los bits 32 del cociente.

## <a name="remarks"></a>Notas

El intrínseco `_div64` divide el *dividendo* por el *divisor*. Almacena el resto en el entero de 32 bits al que apunta el *resto*y devuelve los 32 bits del cociente.

El `_div64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_udiv64](udiv64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
