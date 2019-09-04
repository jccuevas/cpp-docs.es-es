---
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5da9ac81cedbdd24e10eb438892f88510c32ca24
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218007"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Específicos de Microsoft**

Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la izquierda según un número de bits especificado por `Shift` y devuelve los 64 bits superiores del resultado.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Parámetros

*LowPart*\
de Los bits 64 bajos de la cantidad de 128 bits que se va a desplazar.

*HighPart*\
de Los bits 64 altos de la cantidad de 128 bits que se va a desplazar.

*Mover*\
de Número de bits que se va a desplazar.

## <a name="return-value"></a>Valor devuelto

Los 64 bits superiores del resultado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__shiftleft128`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El valor de *desplazamiento* es siempre módulo 64, de modo que, por ejemplo, `__shiftleft128(1, 0, 64)`si llama a, la función desplazará los bits de la parte `0` baja a `0` la izquierda y devolverá una parte alta de y no `1` como cabría esperar.

## <a name="example"></a>Ejemplo

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__shiftright128](../intrinsics/shiftright128.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
