---
title: _mm_stream_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_si64x
helpviewer_keywords:
- movnti instruction
- _mm_stream_si64x intrinsic
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
ms.openlocfilehash: f6ed0f2482ecbcdaa4d50034e0d08381768847a2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221747"
---
# <a name="_mm_stream_si64x"></a>_mm_stream_si64x

**Específicos de Microsoft**

Genera la instrucción MOVNTI. Escribe los datos de *origen* en una ubicación de memoria especificada por el *destino*, sin contaminar las cachés.

## <a name="syntax"></a>Sintaxis

```C
void _mm_stream_si64x(
   __int64 * Destination,
   __int64 Source
);
```

### <a name="parameters"></a>Parámetros

*Destino*\
enuncia Puntero a la ubicación en la que se van a escribir los datos de origen.

*Source*\
de Datos que se van a escribir.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_stream_si64x`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```C
// _mm_stream_si64x.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_mm_stream_si64x)

int main()
{
    __int64 val = 0xFFFFFFFFFFFFI64;
    __int64 a[10];

    memset(a, 0, sizeof(a));
    _mm_stream_si64x(a+1, val);
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff 0 0
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
