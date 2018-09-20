---
title: _mm_insert_si64, _mm_inserti_si64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f859b461a2072afabbe48126eba94e0a3ed470a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403871"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64

**Específicos de Microsoft**

Genera el `insertq` instrucciones para insertar los bits de su segundo operando en su primer operando.

## <a name="syntax"></a>Sintaxis

```
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

#### <a name="parameters"></a>Parámetros

*Source1*<br/>
[in] Un campo de 128 bits con datos de entrada en sus en la que se van a insertar un campo de 64 bits inferiores.

*Source2*<br/>
[in] Un campo de 128 bits con los datos que se va a insertar en sus bits inferiores.  Para `_mm_insert_si64`, también contiene un descriptor de campo en sus partes alta.

*Longitud*<br/>
[in] Una constante entera que especifica la longitud del campo se va a insertar.

*Index*<br/>
[in] Una constante entera que especifica el índice del bit menos significativo del campo en el que se van a insertar datos.

## <a name="return-value"></a>Valor devuelto

Un campo de 128 bits cuyos 64 bits inferiores contienen los 64 bits inferiores originales de `Source1` con el campo de bits especificado reemplazados por los bits inferiores del `Source2`. Los 64 bits superiores del valor devuelto son indefinidos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca genera el `insertq` instrucciones para insertar los bits de `Source2` en `Source1`. Hay dos versiones de este intrínsecas: `_mm_inserti_si64`, es la versión inmediata, y `_mm_insert_si64` es lo que no es inmediato.  Cada versión extrae un campo de bits de una longitud dada Source2 y lo inserta en Source1.  Los bits extraídos son los bits menos significativos de Source2.  El Source1 de campo en el que se van a insertar estos bits se define mediante la longitud y el índice de su bit menos significativo.  Los valores de la longitud y el índice se toman mod 64, -1 y 127 se interpreta como 63. Si la suma del índice de bits (reducida) y de longitud de campo (reducida) es mayor que 64, los resultados son indefinidos. Un valor de cero para la longitud de campo se interpreta como 64.  Si el índice del campo de longitud y el bit es ambos cero, 63:0 bits de `Source2` se insertan en `Source1`.  Si la longitud de campo es cero, pero el índice de bits es distinto de cero, los resultados son indefinidos.

En una llamada a _mm_insert_si64, se encuentra la longitud de campo en bits 77:72 de Source2 y el índice de bits 69:64.

Si se llama a `_mm_inserti_si64` con argumentos que el compilador no puede determinar que las constantes de tipo entero, el compilador genera código para empaquetar esos valores en un registro XMM y llamar a `_mm_insert_si64`.

Para determinar la compatibilidad de hardware para el `insertq` llamada la `__cpuid` intrínseca con `InfoType=0x80000001` y comprobar poco 6 de `CPUInfo[2] (ECX)`. Este bit será 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta el código que usa esta función intrínseca en hardware que no es compatible con la `insertq` instrucciones, los resultados son impredecibles.

## <a name="example"></a>Ejemplo

```
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

Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)