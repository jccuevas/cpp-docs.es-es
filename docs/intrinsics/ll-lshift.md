---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024470"
---
# <a name="lllshift"></a>__ll_lshift

**Específicos de Microsoft**

Desplaza el valor de 64 bits proporcionado a la izquierda el número especificado de bits.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parámetros

*Máscara*<br/>
[in] El valor del entero de 64 bits para desplazarse a la izquierda.

*nBit*<br/>
[in] El número de bits del desplazamiento.

## <a name="return-value"></a>Valor devuelto

La máscara desplazado a la izquierda `nBit` bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Si compila un programa con la arquitectura de 64 bits y `nBit` es superior a 63, es el número de bits del desplazamiento `nBit` módulo 64. Si compila un programa con la arquitectura de 32 bits y `nBit` es mayor que 31, el número de bits del desplazamiento es `nBit` módulo 32.

El `ll` en el nombre indica que esta es una operación en `long long` (`__int64`).

## <a name="example"></a>Ejemplo

```
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

```
10000
```

**Tenga en cuenta** hay ninguna versión sin signo de la operación de desplazamiento a la izquierda. Esto es porque `__ll_lshift` ya usa un parámetro de entrada sin signo. A diferencia de desplazamiento a la derecha, no hay ninguna dependencia de inicio de sesión para el desplazamiento a la izquierda, porque el bit menos significativo en el resultado siempre se establece en cero, independientemente del signo del valor desplazado a la.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)