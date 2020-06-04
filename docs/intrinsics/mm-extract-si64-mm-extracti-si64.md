---
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: cfd7029966c29f876f0e4f671830e20e2eacc940
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217402"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64, _mm_extracti_si64

**Específicos de Microsoft**

Genera la `extrq` instrucción para extraer los bits especificados de los bits 64 bajos de su primer argumento.

## <a name="syntax"></a>Sintaxis

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>Parámetros

*Source*\
de Un campo de 128 bits con datos de entrada en sus 64 bits inferiores.

*Scripto*\
de Campo de 128 bits que describe el campo de bits que se va a extraer.

*Longitud*\
de Entero que especifica la longitud del campo que se va a extraer.

*Ajustar*\
de Un entero que especifica el índice del campo que se va a extraer.

## <a name="return-value"></a>Valor devuelto

Un campo de 128 bits con el campo extraído en los bits menos significativos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Estos intrínsecos generan la `extrq` instrucción para extraer bits del *origen*. Hay dos versiones: `_mm_extracti_si64` es la versión inmediata y `_mm_extract_si64` es la no inmediata. Cada versión extrae del *origen* un campo de bits definido por su longitud y el índice de su bit menos significativo. Los valores de la longitud y el índice se toman como mod 64, por lo que-1 y 127 se interpretan como 63. Si la suma del índice (reducido) y la longitud del campo (reducida) es mayor que 64, los resultados son indefinidos. Un valor de cero para la longitud de campo se interpreta como 64. Si la longitud del campo y el índice de bits son cero, se extraen los bits 63:0 del *origen* . Si la longitud del campo es cero, pero el índice de bits es distinto de cero, los resultados son indefinidos.

En una llamada a `_mm_extract_si64`, el descriptor contiene el índice en bits 13:8 y la longitud del campo de los datos que se van a extraer en bits 5:0.

Si llama `_mm_extracti_si64` a con argumentos que el compilador no puede determinar como constantes de tipo entero, el compilador genera código para empaquetar esos valores en un registro XMM ( `_mm_extract_si64`descriptor) y para llamar a.

Para determinar la compatibilidad de hardware `extrq` de la instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 6 de. Este bit será 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta código que usa este hardware intrínseco que no admite la `extrq` instrucción, los resultados son imprevisibles.

## <a name="example"></a>Ejemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**FIN de Específicos de Microsoft**

Partes con Copyright 2007 de Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
