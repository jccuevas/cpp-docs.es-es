---
title: _BitScanReverse, _BitScanReverse64
ms.date: 09/02/2019
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
ms.openlocfilehash: 848c153967e5581f08f1d499a28ab282ee2602df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216945"
---
# <a name="_bitscanreverse-_bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Específicos de Microsoft**

Buscar los datos de máscara de bit más significativo (MSB) a bit menos significativo (LSB) para un bit establecido (1).

## <a name="syntax"></a>Sintaxis

```C
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

### <a name="parameters"></a>Parámetros

*Ajustar*\
enuncia Se carga con la posición de bit del primer bit establecido (1).

*Máscara*\
de Valor de 32 bits o 64 bits en el que se va a buscar.

## <a name="return-value"></a>Valor devuelto

Distinto de cero si se estableció `Index`, o 0 si no se encuentra ningún bit establecido.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Encabezado|
|---------------|------------------|------------|
|`_BitScanReverse`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_BitScanReverse64`|ARM64, x64|\<intrin.h>|

## <a name="example"></a>Ejemplo

```cpp
// BitScanReverse.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanReverse)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanReverse(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

```Input
12
```

```Output
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
