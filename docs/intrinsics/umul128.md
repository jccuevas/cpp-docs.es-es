---
title: "_umul128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__umul128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__umul128 intrinsic"
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _umul128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Multiplica dos enteros no firmados de 64 bits pasados como los dos primeros argumentos y pone los 64 bits superiores del producto en el entero de 64 bits no firmado que señala `HighProduct` y devuelve los 64 bits inferiores del producto.  
  
## Sintaxis  
  
```  
unsigned __int64 _umul128(     unsigned __int64 Multiplier,     unsigned __int64 Multiplicand,     unsigned __int64 *HighProduct  );  
```  
  
#### Parámetros  
 \[in\] `Multiplier`  
 El primer entero de 64 bits que se multiplica.  
  
 \[in\] `Multiplicand`  
 El segundo entero de 64 bits que se multiplica.  
  
 \[out\] `HighProduct`  
 Los 64 bits superiores del producto.  
  
## Valor devuelto  
 Los 64 bits inferiores del producto.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_umul128`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## Ejemplo  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
  **0xfffffffffffffff \* 0xf0000000 \= 0xeffffffffffffff10000000**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)