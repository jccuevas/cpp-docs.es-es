---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217347"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Específicos de Microsoft**

Escribe datos de 32 bits en una ubicación de memoria sin contaminar las cachés.

## <a name="syntax"></a>Sintaxis

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Parámetros

*Destino*\
enuncia Puntero a la ubicación donde se escriben los datos de origen.

*Source*\
de Número de 128 bits que contiene el `float` valor que se va a escribir en sus 32 bits inferiores.

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El intrínseco genera la `movntss` instrucción. Para determinar la compatibilidad de hardware para esta instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 6 de. Este bit es 1 cuando se admite la instrucción y 0 en caso contrario.

Si ejecuta código que usa el `_mm_stream_ss` intrínseco en hardware que no admite la `movntss` instrucción, los resultados son imprevisibles.

## <a name="example"></a>Ejemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**FIN de Específicos de Microsoft**

Partes con Copyright 2007 de Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
