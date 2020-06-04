---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: ad17991d84acb7e531baf9435610ebd566197a22
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217501"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Específicos de Microsoft**

Desplaza un valor de 64 bits especificado por el primer parámetro de la derecha, por un número de bits especificado por el segundo parámetro.

## <a name="syntax"></a>Sintaxis

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parámetros

*Máscara*\
de Valor entero de 64 bits que se va a desplazar hacia la derecha.

*nBit*\
de Número de bits que se van a desplazar, módulo 64 en x64 y módulo 32 en x86.

## <a name="return-value"></a>Valor devuelto

Máscara desplazada por `nBit` bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Si el segundo parámetro es mayor que 64 en x64 (32 en x86), ese número se toma como módulo 64 (32 en x86) para determinar el número de bits que se va a desplazar. El `ll` prefijo indica que se trata de una `long long`operación en, otro `__int64`nombre para, el tipo entero con signo de 64 bits.

## <a name="example"></a>Ejemplo

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Salida

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> Si `_ull_rshift` se ha usado, el MSB del valor desplazado a la derecha habría sido cero, por lo que el resultado deseado no se habría obtenido en el caso de un valor negativo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
