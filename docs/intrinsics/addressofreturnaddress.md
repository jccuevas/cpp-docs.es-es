---
title: _AddressOfReturnAddress | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05f6632b21d0534ea81ef285333f9665bbb25b9a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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
|`_AddressOfReturnAddress`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Cuando `_AddressOfReturnAddress` se utiliza en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene el `_AddressOfReturnAddress` llamada se compila como una función nativa. Cuando se compila una función como administrado llama a la función que contiene `_AddressOfReturnAddress`, `_AddressOfReturnAddress` posible que no funcionen según lo previsto.  
  
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
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)