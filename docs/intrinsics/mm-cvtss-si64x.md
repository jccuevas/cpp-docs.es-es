---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 6079ed7846a35ff16355f0341d63430f9846057f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217438"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Específicos de Microsoft**

Genera la versión extendida de x64 del número de punto flotante de precisión sencilla escalar a la instrucción entera`cvtss2si`de 64 bits ().

## <a name="syntax"></a>Sintaxis

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parámetros

*value*\
de `__m128` Estructura que contiene los valores de punto flotante.

## <a name="return-value"></a>Valor devuelto

Entero de 64 bits, el resultado de la conversión del primer valor de punto flotante en un entero.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El primer elemento del valor de la estructura se convierte en un entero y se devuelve. Los bits de control de redondeo de MXCSR se usan para determinar el comportamiento de redondeo. El modo de redondeo predeterminado es redondear a la más cercana, redondeando al número par si la parte decimal es 0,5. Dado que `__m128` la estructura representa un registro XMM, el intrínseco toma un valor del registro XMM y lo escribe en la memoria del sistema.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__m128d](../cpp/m128d.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
