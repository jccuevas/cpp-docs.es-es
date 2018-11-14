---
title: _mm_stream_sd
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: cf57d485ab3dd268d217b2ef44ff53bcec3d2e63
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518143"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Específicos de Microsoft**

Escribe datos de 64 bits en una ubicación de memoria sin contaminar las memorias caché.

## <a name="syntax"></a>Sintaxis

```
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

#### <a name="parameters"></a>Parámetros

*dest*<br/>
[out] Un puntero a la ubicación donde se escribirán los datos de origen.

*Origen*<br/>
[in] Un valor de 128 bits que contiene el `double` valor que se escribirá en la parte inferior de 64 bits...

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca genera el `movntsd` instrucción. Para determinar la compatibilidad de hardware para esta instrucción, llame a la `__cpuid` intrínseca con `InfoType=0x80000001` y comprobar poco 6 de `CPUInfo[2] (ECX)`. Este bit es 1 si el hardware es compatible con esta instrucción y 0 en caso contrario.

Si ejecuta el código que utiliza el `_mm_stream_sd` intrínseco en hardware que no es compatible con la `movntsd` instrucciones, los resultados son impredecibles.

## <a name="example"></a>Ejemplo

```
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

Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)<br/>
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)