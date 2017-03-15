---
title: "__ull_rshift | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ull_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ull_rshift (función intrínseca)"
  - "__ull_rshift (función intrínseca)"
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __ull_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 en x64, cambia un valor de 64 bits especificado por el primer parámetro a la derecha por varios bits especificado por el segundo parámetro.  
  
## Sintaxis  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### Parámetros  
 \[in\] `mask`  
 El valor entero de 64 bits para desplazar la derecha.  
  
 \[in\] `nBit`  
 El número de bits para desplazarse, el módulo 32 en x86, el módulo y 64 en x64.  
  
## Valor devuelto  
 La máscara se desplaza por los bits de `nBit` .  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__ull_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Si el segundo parámetro es mayor que 31 en x86 \(63 en x64\), ese número es el módulo tomado 32 \(64 en x64\) para determinar el número de bits para desplazarse.  `ull` en el nombre indica `unsigned long long (unsigned __int64)`.  
  
## Ejemplo  
  
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
  
## Output  
  
```  
1  
```  
  
### Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)