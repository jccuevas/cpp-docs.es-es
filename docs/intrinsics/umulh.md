---
title: "__umulh | Microsoft Docs"
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
  - "__umulh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco __umulh"
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __umulh
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Devolver los 64 bits superiores del producto de dos enteros sin signo de 64 bits.  
  
## Sintaxis  
  
```  
unsigned __int64 __umulh(     unsigned __int64 a,     unsigned __int64 b  );  
```  
  
#### Parámetros  
 \[in\] `a`  
 El primer número que se va a multiplicar.  
  
 \[in\] `b`  
 El segundo número que se va a multiplicar.  
  
## Valor devuelto  
 Los 64 bits superiores del resultado de 128 bits de la multiplicación.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__umulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## Ejemplo  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
  **0x10 \* 0xfedcba9876543210 \= 0xfedcba98765432100**    
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)