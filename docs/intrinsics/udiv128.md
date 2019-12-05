---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857988"
---
# <a name="_udiv128"></a>_udiv128

El intrínseco `_udiv128` divide un entero de 128 bits sin signo por un entero de 64 bits sin signo. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_udiv128` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Parameters

 \ *highDividend*
de Los bits 64 altos del dividendo.

*lowDividend* \
de Los bits 64 bajos del dividendo.

 \ *divisor*
de Entero de 64 bits por el que se va a dividir.

*remainder* \
enuncia Los bits enteros de 64 bits del resto.

## <a name="return-value"></a>Valor devuelto

Los bits 64 del cociente.

## <a name="remarks"></a>Notas

Pase los 64 superiores del dividendo de 128 bits en *highDividend*y los 64 bits inferiores en *lowDividend*. Intrínseco divide este valor por el *divisor*. Almacena el resto en el entero de 64 bits sin signo al que apunta el *resto*y devuelve los 64 bits del cociente.

El `_udiv128` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_div128](div128.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
