---
title: _umul128
ms.date: 11/04/2016
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: f7b33767155c4781d131a008d6d42dcc4015d07b
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330520"
---
# <a name="umul128"></a>_umul128

**Específicos de Microsoft**

Multiplica dos enteros no firmados de 64 bits pasados como los dos primeros argumentos y pone los 64 bits superiores del producto en el entero de 64 bits no firmado que señala `HighProduct` y devuelve los 64 bits inferiores del producto.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

#### <a name="parameters"></a>Parámetros

*Multiplicador*<br/>
[in] El primer entero de 64 bits se va a multiplicar.

*Multiplicando*<br/>
[in] El segundo entero de 64 bits se va a multiplicar.

*HighProduct*<br/>
[out] Los 64 bits superiores del producto.

## <a name="return-value"></a>Valor devuelto

Los 64 bits inferiores del producto.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_umul128`|ARM, x64|\<INTRIN.h >|

## <a name="example"></a>Ejemplo

```
// umul128.c
// processor: IPF, x64

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

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)