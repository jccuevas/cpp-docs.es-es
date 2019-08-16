---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390157"
---
# <a name="udiv64"></a>_udiv64

El `_udiv64` intrínseco divide un entero de 64 bits sin signo en un entero de 32 bits sin signo. El valor devuelto contiene el cociente y el intrínseco devuelve el resto a través de un parámetro de puntero. `_udiv64` es **específico de Microsoft**.

## <a name="syntax"></a>Sintaxis

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parámetros

*dividend*<br/>
[in] Entero sin signo de 64 bits se va a dividir.

*divisor*<br/>
[in] Entero sin signo de 32 bits para dividir por.

*remainder*<br/>
[out] El resto entero de 32 bits sin signo.

## <a name="return-value"></a>Valor devuelto

Los 32 bits del cociente.

## <a name="remarks"></a>Comentarios

El `_udiv64` divide intrínseco *dividendo* por *divisor*. Almacena el resto en el entero sin signo de 32 bits que señala *resto*y devuelve los 32 bits del cociente.

El `_udiv64` intrínseco está disponible a partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Vea también

[_div64](div64.md) \
[Intrínsecos del compilador](compiler-intrinsics.md)
