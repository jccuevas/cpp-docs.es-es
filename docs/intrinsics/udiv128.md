---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390170"
---
# <a name="udiv128"></a>_udiv128

El `_udiv128` intrínseco divide un entero de 128 bits sin signo por un entero de 64 bits sin signo. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_udiv128` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Parámetros

*highDividend* \
[in] Los 64 bits superiores del dividendo.

*lowDividend* \
[in] Los 64 bits inferiores del dividendo.

*divisor* \
[in] Entero de 64 bits que se va a dividir.

*remainder* \
[out] Los bits de entero de 64 bits del resto.

## <a name="return-value"></a>Valor devuelto

Los 64 bits del cociente.

## <a name="remarks"></a>Comentarios

Pasar los 64 bits superiores del dividendo 128 bits en *highDividend*y los 64 bits inferiores en *lowDividend*. La función intrínseca divide este valor por *divisor*. Almacena el resto en el entero sin signo de 64 bits que señala *resto*y devuelve los 64 bits del cociente.

El `_udiv128` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_div128](div128.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
