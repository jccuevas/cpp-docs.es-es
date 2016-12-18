---
title: "_AddressOfReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_AddressOfReturnAddress_cpp"
  - "_AddressOfReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AddressOfReturnAddress (función intrínseca)"
  - "AddressOfReturnAddress (función intrínseca)"
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _AddressOfReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Proporciona la dirección de la ubicación de memoria que contiene la dirección de devolución de la función actual.  Esta dirección no puede utilizar para tener acceso a otras ubicaciones de memoria \(por ejemplo, los argumentos de la función\).  
  
## Sintaxis  
  
```  
void * _AddressOfReturnAddress();  
```  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_AddressOfReturnAddress`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Cuando `_AddressOfReturnAddress` se utiliza en un programa compilado con [\/clr](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene la llamada de `_AddressOfReturnAddress` se compiló como función nativa.  Cuando una función compilada como llamadas administradas en la función que contiene `_AddressOfReturnAddress`, `_AddressOfReturnAddress` podría comportarse como se espera.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
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
  
  **0012FF78 00401058 00401058**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)