---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858001"
---
# <a name="_udiv64"></a>_udiv64

El intrínseco `_udiv64` divide un entero de 64 bits sin signo por un entero de 32 bits sin signo. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_udiv64` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parameters

*dividend*\
de Entero de 64 bits sin signo que se va a dividir.

\ *divisor*
de Entero de 32 bits sin signo que se va a dividir.

*remainder*\
enuncia Entero de 32 bits sin signo restante.

## <a name="return-value"></a>Valor devuelto

Los bits 32 del cociente.

## <a name="remarks"></a>Notas

El intrínseco `_udiv64` divide el *dividendo* por el *divisor*. Almacena el resto en el entero de 32 bits sin signo al que apunta el *resto*y devuelve los 32 bits del cociente.

El `_udiv64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_div64](div64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
