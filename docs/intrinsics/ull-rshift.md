---
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: e914a019877482058c6b2842d3138cda02f1e228
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219705"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Específicos de Microsoft**

en x64, desplaza un valor de 64 bits especificado por el primer parámetro hacia la derecha un número de bits especificado por el segundo parámetro.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

### <a name="parameters"></a>Parámetros

*máscara*\
de Valor entero de 64 bits que se va a desplazar hacia la derecha.

*nBit*\
de Número de bits que se van a desplazar, módulo 32 en x86 y módulo 64 en x64.

## <a name="return-value"></a>Valor devuelto

Máscara desplazada por `nBit` bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Si el segundo parámetro es mayor que 31 en x86 (63 en x64), ese número se toma como módulo 32 (64 en x64) para determinar el número de bits que se va a desplazar. En el nombre de indica `unsigned long long (unsigned __int64)`. `ull`

## <a name="example"></a>Ejemplo

```cpp
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

```Output
1
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
