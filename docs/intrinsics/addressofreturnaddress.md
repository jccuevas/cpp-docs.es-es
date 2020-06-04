---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221077"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Específicos de Microsoft**

Proporciona la dirección de la ubicación de memoria que contiene la dirección de devolución de la función actual. No se puede usar esta dirección para tener acceso a otras ubicaciones de memoria (por ejemplo, los argumentos de la función).

## <a name="syntax"></a>Sintaxis

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64, ARM, ARM64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Cuando `_AddressOfReturnAddress` se usa en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene `_AddressOfReturnAddress` la llamada se compila como una función nativa. Cuando una función compilada como llamada administrada en `_AddressOfReturnAddress`la `_AddressOfReturnAddress` función que contiene, podría no tener el comportamiento esperado.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
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

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
