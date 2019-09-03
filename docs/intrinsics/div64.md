---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 1d05c5d6e25540a5de1b2f8231697c9a738759ce
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216765"
---
# <a name="_div64"></a>_div64

`_div64` Intrínseco divide un entero de 64 bits por un entero de 32 bits. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_div64`es **específico de Microsoft**.

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
de Entero de 64 bits que se va a dividir.

*divisor* \
de Entero de 32 bits por el que se va a dividir.

*remainder* \
enuncia Los bits enteros de 32 bits del resto.

## <a name="return-value"></a>Valor devuelto

Los bits 32 del cociente.

## <a name="remarks"></a>Comentarios

Intrínseco `_div64` divide el *dividendo* por el divisor. Almacena el resto en el entero de 32 bits al que apunta el *resto*y devuelve los 32 bits del cociente.

El `_div64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Encabezado|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_udiv64](udiv64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
