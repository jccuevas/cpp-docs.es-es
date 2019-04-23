---
title: __ll_rshift
ms.date: 11/04/2016
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: e39f8fe797467569077dd24baf49670607915107
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041025"
---
# <a name="llrshift"></a>__ll_rshift

**Específicos de Microsoft**

Desplaza un valor de 64 bits especificado por el primer parámetro a la derecha el número de bits especificado por el segundo parámetro.

## <a name="syntax"></a>Sintaxis

```
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parámetros

*Máscara*<br/>
[in] El valor entero de 64-bit a desplazar a la derecha.

*nBit*<br/>
[in] El número de bits de desplazamiento, módulo 64 en x64 y 32 en x86 de módulo.

## <a name="return-value"></a>Valor devuelto

Desplace la máscara `nBit` bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Si el segundo parámetro es mayor que 64 en x64 (32 en x86), se toma ese número módulo 64 (32 en x86) para determinar el número de bits del desplazamiento. El `ll` prefijo indica que esta es una operación en `long long`, otro nombre para `__int64`, el tipo entero con signo de 64 bits.

## <a name="example"></a>Ejemplo

```
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

```
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

**Tenga en cuenta** si `_ull_rshift` ha sido utilizado, el MSB del valor desplazado a la derecha habría sido cero, por lo que el resultado deseado no habría obtenido en el caso de un valor negativo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)