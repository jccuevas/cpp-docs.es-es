---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221813"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Específicos de Microsoft**

Desplaza el valor de 64 bits proporcionado a la izquierda el número de bits especificado.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parámetros

*Máscara*\
de Valor entero de 64 bits que se va a desplazar a la izquierda.

*nBit*\
de Número de bits que se va a desplazar.

## <a name="return-value"></a>Valor devuelto

Máscara desplazada a la `nBit` izquierda por bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Si compila el programa para la arquitectura de 64 bits y `nBit` es superior a 63, el número de bits que se va a desplazar es `nBit` módulo 64. Si compila el programa para la arquitectura de 32 bits y `nBit` es mayor que 31, el número de bits que se va a desplazar es `nBit` módulo 32.

En el nombre indica que se trata de una operación de `long long` (`__int64`). `ll`

## <a name="example"></a>Ejemplo

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Salida

```Output
10000
```

> [!NOTE]
> No hay ninguna versión sin firmar de la operación de desplazamiento a la izquierda. Esto se debe `__ll_lshift` a que ya usa un parámetro de entrada sin signo. A diferencia del desplazamiento a la derecha, no hay ninguna dependencia de signo para el desplazamiento a la izquierda, ya que el bit menos significativo en el resultado siempre se establece en cero, independientemente del signo del valor desplazado.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
