---
title: _umul128
ms.date: 09/02/2019
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: 205f0f7f9046ede624bb09e18d8ede32fadbc3de
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219693"
---
# <a name="_umul128"></a>_umul128

**Específicos de Microsoft**

Multiplica dos enteros no firmados de 64 bits pasados como los dos primeros argumentos y pone los 64 bits superiores del producto en el entero de 64 bits no firmado que señala `HighProduct` y devuelve los 64 bits inferiores del producto.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

### <a name="parameters"></a>Parámetros

*Multiplicador*\
de Primer entero de 64 bits que se va a multiplicar.

*Multiplicando*\
de Segundo entero de 64 bits que se va a multiplicar.

*HighProduct*\
enuncia Los altos 64 bits del producto.

## <a name="return-value"></a>Valor devuelto

Los 64 bits inferiores del producto.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Encabezado|
|---------------|------------------|------------|
|`_umul128`|x64|\<intrin.h>|

## <a name="example"></a>Ejemplo

```C
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
