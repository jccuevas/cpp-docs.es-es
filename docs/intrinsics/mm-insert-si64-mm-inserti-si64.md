---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221780"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Específicos de Microsoft**

Genera la `insertq` instrucción para insertar bits de su segundo operando en su primer operando.

## <a name="syntax"></a>Sintaxis

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>Parámetros

*Source1*\
de Un campo de 128 bits con datos de entrada en sus 64 bits inferiores, en el que se insertará un campo.

*Source2*\
de Un campo de 128 bits que tiene los datos que se van a insertar en los bits bajos.  Para `_mm_insert_si64`, también contiene un descriptor de campo en sus bits altos.

*Longitud*\
de Una constante de tipo entero que especifica la longitud del campo que se va a insertar.

*Ajustar*\
de Una constante de tipo entero que especifica el índice del bit menos significativo del campo en el que se insertarán los datos.

## <a name="return-value"></a>Valor devuelto

Un campo de 128 bits, cuyos bits de 64 inferiores contienen los bits bajos de 64 originales de *Source1*, con el campo de bits especificado reemplazado por los bits bajos de *source2*. Los 64 superiores del valor devuelto son indefinidos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Estos intrínsecos generan la `insertq` instrucción para insertar bits de *source2* en *Source1*. Hay dos versiones: `_mm_inserti_si64`, es la versión inmediata y `_mm_insert_si64` es el no inmediato. Cada versión extrae un campo de bits de una longitud determinada de source2 y lo inserta en Source1.  Los bits extraídos son los bits menos significativos de source2.  El campo Source1 en el que se insertarán estos bits se define con la longitud y el índice de su bit menos significativo.  Los valores de la longitud y el índice se toman como mod 64, por lo que-1 y 127 se interpretan como 63. Si la suma del índice de bits (reducido) y la longitud del campo (reducida) es mayor que 64, los resultados son indefinidos. Un valor de cero para la longitud de campo se interpreta como 64. Si la longitud del campo y el índice de bits son cero, se insertan bits 63:0 de *source2* en *Source1*. Si la longitud del campo es cero, pero el índice de bits es distinto de cero, los resultados son indefinidos.

En una llamada a _mm_insert_si64, la longitud del campo se incluye en los bits 77:72 de source2 y en el índice en bits 69:64.

Si llama `_mm_inserti_si64` a con argumentos que el compilador no puede determinar como constantes de tipo entero, el compilador genera código para empaquetar esos valores en un `_mm_insert_si64`registro XMM y para llamar a.

Para determinar la compatibilidad de hardware `insertq` de la instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 6 de. Este bit es 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta código que usa el intrínseco en hardware que no admite la `insertq` instrucción, los resultados son imprevisibles.

## <a name="example"></a>Ejemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**FIN de Específicos de Microsoft**

Partes con Copyright 2007 de Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
