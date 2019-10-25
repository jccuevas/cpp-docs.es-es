---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217454"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Específicos de Microsoft**

Genera la versión extendida de 64 bits del entero de 64 bits para la instrucción de valor de punto flotante (`cvtsi2ss`) de precisión sencilla escalar.

## <a name="syntax"></a>Sintaxis

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Parámetros

*un*\
de `__m128` Estructura que contiene cuatro valores de punto flotante de precisión sencilla.

*b*\
de Entero de 64 bits que se va a convertir en un valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

`__m128` Estructura cuyo primer valor de punto flotante es el resultado de la conversión. Los otros tres valores se copian sin cambios desde.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

La `__m128` estructura representa un registro XMM, por lo que el intrínseco permite que el valor *b* de la memoria del sistema se mueva a un registro XMM.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__m128](../cpp/m128.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
