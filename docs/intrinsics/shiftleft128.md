---
title: "__shiftleft128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__shiftleft128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__shiftleft128 intrinsic"
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# __shiftleft128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la izquierda según un número de bits especificado por `Shift` y devuelve los 64 bits superiores del resultado.  
  
## Sintaxis  
  
```  
unsigned __int64 __shiftleft128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### Parámetros  
 \[in\] `LowPart`  
 Los 64 bits inferiores de la cantidad de 128 bits que se va a desplazar.  
  
 \[in\] `HighPart`  
 Los 64 bits superiores de la cantidad de 128 bits que se va a desplazar.  
  
 \[in\] `Shift`  
 El número de bits que se va a desplazar.  
  
## Valor devuelto  
 Los 64 bits superiores del resultado.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__shiftleft128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El valor `Shift` es siempre módulo 64 para que, por ejemplo, si se llama a `__shiftleft128(1, 0, 64)`, la función desplace los bits `0` de la parte baja a la izquierda y devuelva una parte alta de `0` en vez de `1`, como cabría esperar.  
  
## Ejemplo  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
  **0x100000000000000001 \<\< 1 \= 0x200000000000000002**  
**0x100000000000000001 \>\> 1 \= 0x080000000000000000**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_\_shiftright128](../intrinsics/shiftright128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)