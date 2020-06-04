---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 7f0c6457cc0806a0f1764300cffa1c9878b8a600
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217363"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Específicos de Microsoft**

Escribe datos de 64 bits en una ubicación de memoria sin contaminar las cachés.

## <a name="syntax"></a>Sintaxis

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>Parámetros

*Dest*\
enuncia Puntero a la ubicación donde se escribirán los datos de origen.

*Source*\
de Valor de 128 bits que contiene el `double` valor que se va a escribir en sus 64 bits inferiores.

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El intrínseco genera la `movntsd` instrucción. Para determinar la compatibilidad de hardware para esta instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 6 de. Este bit es 1 si el hardware es compatible con esta instrucción y 0 de lo contrario.

Si ejecuta código que usa el `_mm_stream_sd` intrínseco en hardware que no admite la `movntsd` instrucción, los resultados son imprevisibles.

## <a name="example"></a>Ejemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**FIN de Específicos de Microsoft**

Partes con Copyright 2007 de Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
