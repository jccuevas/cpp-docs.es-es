---
title: "FILETIME (Estructura) | Microsoft Docs"
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
  - "FILETIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FILETIME (estructura)"
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FILETIME (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `FILETIME` es un valor de 64 bits que representa el número de 100 intervalos de nanosegundo desde el 1 de enero de 1601.  
  
## Sintaxis  
  
```  
  
      typedef struct _FILETIME {  
   DWORD dwLowDateTime;   /* low 32 bits  */  
   DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### Parámetros  
 *dwLowDateTime*  
 Especifica los bits de low 32 del tiempo del archivo.  
  
 *dwHighDateTime*  
 Especifica los bits de alto y 32 del tiempo del archivo.  
  
## Requisitos  
 **Encabezado:** windef.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)