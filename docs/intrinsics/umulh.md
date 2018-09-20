---
title: __umulh | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umulh
dev_langs:
- C++
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 840dc430189a81108d92aa692e7e5b9845375910
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430831"
---
# <a name="umulh"></a>__umulh

**Específicos de Microsoft**

Devolver los 64 bits superiores del producto de dos enteros sin signo de 64 bits.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __umulh( 
   unsigned __int64 a, 
   unsigned __int64 b 
);
```

#### <a name="parameters"></a>Parámetros

*a*<br/>
[in] El primer número a multiplicar.

*b*<br/>
[in] El segundo número a multiplicar.

## <a name="return-value"></a>Valor devuelto

Los 64 bits superiores del resultado de 128 bits de la multiplicación.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__umulh`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Estas rutinas solo están disponibles como intrínsecos.

## <a name="example"></a>Ejemplo

```
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)