---
title: __ull_rshift
ms.date: 11/04/2016
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: 5d62ec1526aff595c14a53e9eca43a7a3118c8fa
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034529"
---
# <a name="ullrshift"></a>__ull_rshift

**Específicos de Microsoft**

en x64, desplaza un valor de 64 bits especificado por el primer parámetro a la derecha el número de bits especificado por el segundo parámetro.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

#### <a name="parameters"></a>Parámetros

*Máscara*<br/>
[in] El valor entero de 64-bit a desplazar a la derecha.

*nBit*<br/>
[in] El número de bits del desplazamiento de módulo 32 en x86 y módulo 64 en x64.

## <a name="return-value"></a>Valor devuelto

Desplace la máscara `nBit` bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Si el segundo parámetro es mayor que 31 en x86 (63 en x64), que se toma el número de módulo 32 (64 en x64) para determinar el número de bits del desplazamiento. El `ull` en el nombre indica `unsigned long long (unsigned __int64)`.

## <a name="example"></a>Ejemplo

```
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

## <a name="output"></a>Salida

```
1
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)