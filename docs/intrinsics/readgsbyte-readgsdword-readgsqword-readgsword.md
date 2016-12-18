---
title: "__readgsbyte, __readgsdword, __readgsqword, __readgsword | Microsoft Docs"
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
  - "__readgsbyte"
  - "__readgsdword"
  - "__readgsqword"
  - "__readgsword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readgsword (función instrínseca)"
  - "__readgsdword (función instrínseca)"
  - "__readgsqword (función instrínseca)"
  - "__readgsbyte (función instrínseca)"
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readgsbyte, __readgsdword, __readgsqword, __readgsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lea la memoria de una ubicación especificada por un desplazamiento en relación con el principio del segmento de GS.  
  
## Sintaxis  
  
```  
unsigned char __readgsbyte(   
   unsigned long Offset   
);  
unsigned short __readgsword(   
   unsigned long Offset   
);  
unsigned long __readgsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readgsqword(   
   unsigned long Offset   
);  
```  
  
#### Parámetros  
 \[in\] `Offset`  
 El desplazamiento desde el inicio de `GS` para leer de.  
  
## Valor devuelto  
 El contenido de la memoria de bytes, la palabra, la doble palabra, o de quadword \(como se indica por el nombre de la función llamada\) en la ubicación `GS:[``Offset``]`.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__readgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Estos intrínseco solo están disponibles en modo kernel, y rutinas sólo están disponibles como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_writegsbyte, \_\_writegsdword, \_\_writegsqword, \_\_writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)