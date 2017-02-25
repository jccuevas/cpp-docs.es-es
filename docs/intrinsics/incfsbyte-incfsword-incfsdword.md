---
title: "__incfsbyte, __incfsword, __incfsdword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__incfsword"
  - "__incfsbyte_cpp"
  - "__incfsbyte"
  - "__incfsdword"
  - "__incfsword_cpp"
  - "__incfsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__incfsword (función intrínseca)"
  - "__incfsdword (función intrínseca)"
  - "__incfsbyte (función intrínseca)"
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# __incfsbyte, __incfsword, __incfsdword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Agregue uno al valor en una ubicación de memoria especificada por un desplazamiento en relación con el principio del segmento de `FS` .  
  
## Sintaxis  
  
```  
void __incfsbyte(   
   unsigned long Offset   
);  
void __incfsword(   
   unsigned long Offset   
);  
void __incfsdword(   
   unsigned long Offset  
);  
```  
  
#### Parámetros  
 \[in\] `Offset`  
 El desplazamiento desde el inicio de `FS`.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__incfsbyte`|x86|  
|`__incfsword`|x86|  
|`__incfsdword`|x86|  
  
## Comentarios  
 Estos intrínseco solo están disponibles en modo kernel, y rutinas sólo están disponibles como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_addfsbyte, \_\_addfsword, \_\_addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)   
 [\_\_readfsbyte, \_\_readfsdword, \_\_readfsqword, \_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [\_\_writefsbyte, \_\_writefsdword, \_\_writefsqword, \_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)