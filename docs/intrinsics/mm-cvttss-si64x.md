---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 69016a4e23b020b2c4c79c6b97a5a76f2b2dc028
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217418"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Específicos de Microsoft**

Emite la versión extendida de 64 bits del número de punto flotante de precisión sencilla de conversión con truncamiento a la instrucción entera de 64`cvttss2si`bits ().

## <a name="syntax"></a>Sintaxis

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parámetros

*value*\
de `__m128` Estructura que contiene valores de punto flotante de precisión sencilla.

## <a name="return-value"></a>Valor devuelto

Resultado de la conversión del primer valor de punto flotante en un entero de 64 bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

La función intrínseca solo se `_mm_cvtss_si64x` diferencia de en que las conversiones inexactas se truncan hacia cero. Dado que `__m128` la estructura representa un registro XMM, la instrucción generada mueve los datos desde un registro XMM a la memoria del sistema.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__m128](../cpp/m128.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
