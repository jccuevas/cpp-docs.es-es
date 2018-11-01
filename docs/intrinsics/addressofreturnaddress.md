---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 678128c4b09b083b4afe3a86c9b2315eb3c87b1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584489"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Específicos de Microsoft**

Proporciona la dirección de la ubicación de memoria que contiene la dirección de devolución de la función actual. Esta dirección no puede usarse para tener acceso a otras ubicaciones de memoria (por ejemplo, los argumentos de función).

## <a name="syntax"></a>Sintaxis

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Cuando `_AddressOfReturnAddress` se utiliza en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene el `_AddressOfReturnAddress` llamada se compila como una función nativa. Cuando se compila una función como administrado llama a la función que contiene `_AddressOfReturnAddress`, `_AddressOfReturnAddress` podrían no funcionar según lo previsto.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)