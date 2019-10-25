---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219683"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` Intrínseco divide un entero de 64 bits sin signo por un entero de 32 bits sin signo. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_udiv64`es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parámetros

*dividend*\
de Entero de 64 bits sin signo que se va a dividir.

*divisor*\
de Entero de 32 bits sin signo que se va a dividir.

*remainder*\
enuncia Entero de 32 bits sin signo restante.

## <a name="return-value"></a>Valor devuelto

Los bits 32 del cociente.

## <a name="remarks"></a>Comentarios

Intrínseco `_udiv64` divide el *dividendo* por el divisor. Almacena el resto en el entero de 32 bits sin signo al que apunta el *resto*y devuelve los 32 bits del cociente.

El `_udiv64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Encabezado|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_div64](div64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
