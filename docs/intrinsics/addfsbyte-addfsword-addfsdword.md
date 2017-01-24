---
title: "__addfsbyte, __addfsword, __addfsdword | Microsoft Docs"
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
  - "__addfsbyte_cpp"
  - "__addfsdword"
  - "__addfsword_cpp"
  - "__addfsbyte"
  - "__addfsword"
  - "__addfsdword_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__addfsdword (función intrínseca)"
  - "__addfsword (función intrínseca)"
  - "__addfsbyte(función intrínseca)"
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __addfsbyte, __addfsword, __addfsdword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Agregar un valor a una ubicación de memoria especificada por un desplazamiento en relación con el principio del segmento de `FS` .  
  
## Sintaxis  
  
```  
void __addfsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addfsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addfsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
```  
  
#### Parámetros  
 \[in\] `Offset`  
 El desplazamiento desde el inicio de `FS`.  
  
 \[in\] `Data`  
 El valor que se va a agregar a la ubicación de memoria.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__addfsbyte`|x86|  
|`__addfsword`|x86|  
|`__addfsdword`|x86|  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_incfsbyte, \_\_incfsword, \_\_incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)   
 [\_\_readfsbyte, \_\_readfsdword, \_\_readfsqword, \_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [\_\_writefsbyte, \_\_writefsdword, \_\_writefsqword, \_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)