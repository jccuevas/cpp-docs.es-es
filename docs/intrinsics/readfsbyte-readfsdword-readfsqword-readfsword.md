---
title: "__readfsbyte, __readfsdword, __readfsqword, __readfsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readfsword"
  - "__readfsdword"
  - "__readfsbyte"
  - "__readfsqword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readfsword (función intrínseca)"
  - "readfsword (función intrínseca)"
  - "__readfsdword (función intrínseca)"
  - "readfsbyte (función intrínseca)"
  - "__readfsbyte (función intrínseca)"
  - "readfsdword (función intrínseca)"
  - "readfsqword (función intrínseca)"
  - "__readfsqword (función intrínseca)"
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readfsbyte, __readfsdword, __readfsqword, __readfsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lea la memoria de una ubicación especificada por un desplazamiento en relación con el principio del segmento de FS.  
  
## Sintaxis  
  
```  
unsigned char __readfsbyte(   
   unsigned long Offset   
);  
unsigned short __readfsword(   
   unsigned long Offset   
);  
unsigned long __readfsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readfsqword(   
   unsigned long Offset   
);  
```  
  
#### Parámetros  
 \[in\] `Offset`  
 El desplazamiento desde el inicio de `FS` para leer de.  
  
## Valor devuelto  
 El contenido de la memoria de bytes, la palabra, la palabra double, o de quadword \(como se indica por el nombre de la función llamada\) en la ubicación `FS:[``Offset``]`.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__readfsbyte`|x86|  
|`__readfsdword`|x86|  
|`__readfsqword`|x86|  
|`__readfsword`|x86|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_writefsbyte, \_\_writefsdword, \_\_writefsqword, \_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)