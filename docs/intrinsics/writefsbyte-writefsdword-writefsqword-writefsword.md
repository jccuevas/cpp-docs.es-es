---
title: "__writefsbyte, __writefsdword, __writefsqword, __writefsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writefsword"
  - "__writefsbyte"
  - "__writefsqword"
  - "__writefsdword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "writefsbyte (función intrínseca)"
  - "__writefsword (función intrínseca)"
  - "writefsqword (función intrínseca)"
  - "writefsdword (función intrínseca)"
  - "__writefsdword (función intrínseca)"
  - "__writefsqword (función intrínseca)"
  - "__writefsbyte (función intrínseca)"
  - "writefsword (función intrínseca)"
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __writefsbyte, __writefsdword, __writefsqword, __writefsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escriba la memoria en una ubicación especificada por un desplazamiento en relación con el principio del segmento de FS.  
  
## Sintaxis  
  
```  
void __writefsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writefsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writefsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writefsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### Parámetros  
 \[in\] `Offset`  
 El desplazamiento desde el inicio de FS a escribir.  
  
 \[in\] `Data`  
 Valor que se va a escribir.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__writefsbyte`|x86|  
|`__writefsword`|x86|  
|`__writefsdword`|x86|  
|`__writefsqword`|x86|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_readfsbyte, \_\_readfsdword, \_\_readfsqword, \_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)