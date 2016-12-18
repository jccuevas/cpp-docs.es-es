---
title: "__shiftright128 | Microsoft Docs"
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
  - "__shiftright128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__shiftright128 intrinsic"
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __shiftright128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la derecha según un número de bits especificado por `Shift` y devuelve los 64 bits inferiores del resultado.  
  
## Sintaxis  
  
```  
unsigned __int64 __shiftright128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### Parámetros  
 \[in\] `LowPart`  
 Los 64 bits inferiores de la cantidad de 128 bits que se va a desplazar.  
  
 \[in\] `HighPart`  
 Los 64 bits superiores de la cantidad de 128 bits que se va a desplazar.  
  
 \[in\] `Shift`  
 El número de bits que se va a desplazar.  
  
## Valor devuelto  
 Los 64 bits inferiores del resultado.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El valor `Shift` es siempre módulo 64 para que, por ejemplo, si se llama a `__shiftright128(0, 1, 64)`, la función desplace los bits `0` de la parte alta a la derecha y devuelva una parte baja de `0` en vez de `1`, como cabría esperar.  
  
## Ejemplo  
 Para ver un ejemplo, consulte [\_\_shiftleft128](../intrinsics/shiftleft128.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_\_shiftleft128](../intrinsics/shiftleft128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)