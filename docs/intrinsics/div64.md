---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982424"
---
# <a name="div64"></a>_div64

El `_div64` intrínseco divide un entero de 64 bits con un entero de 32 bits. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_div64` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parámetros

*dividend* \
[in] Entero de 64 bits que se va a dividir.

*divisor* \
[in] Entero de 32 bits que se va a dividir.

*remainder* \
[out] Los bits de entero de 32 bits del resto.

## <a name="return-value"></a>Valor devuelto

Los 32 bits del cociente.

## <a name="remarks"></a>Comentarios

El `_div64` divide intrínseco *dividendo* por *divisor*. Almacena el resto en el entero de 32 bits que señala *resto*y devuelve los 32 bits del cociente.

El `_div64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_udiv64](udiv64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
