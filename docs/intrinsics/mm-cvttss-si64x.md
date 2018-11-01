---
title: _mm_cvttss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 5c2dd98ad3f74ac56b3656ac5f6f450efc40c088
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522985"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Específicos de Microsoft**

Emite el x64 extendidos versión de la función Convert con el número de punto flotante de precisión sencilla de truncamiento en el entero de 64 bits (`cvttss2si`) instrucción.

## <a name="syntax"></a>Sintaxis

```
__int64 _mm_cvttss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>Parámetros

*valor*<br/>
[in] Un `__m128` estructura que contiene los valores de punto flotante de precisión sencilla.

## <a name="return-value"></a>Valor devuelto

El resultado de la conversión del primer valor de punto flotante en un entero de 64 bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

La función intrínseca difiere `_mm_cvtss_si64x` únicamente en que las conversiones inexactos se truncan hacia cero. Dado que el `__m128` estructura representa un registro XMM, la instrucción genera mueve los datos de un registro XMM en la memoria del sistema.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
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

[__m128](../cpp/m128.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)