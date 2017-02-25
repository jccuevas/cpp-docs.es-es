---
title: "_AtlCreateWndData Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::_AtlCreateWndData"
  - "ATL._AtlCreateWndData"
  - "_AtlCreateWndData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AtlCreateWndData structure"
  - "AtlCreateWndData structure"
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# _AtlCreateWndData Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta estructura contiene datos de la instancia de clase en código de visualización en una ventana de ATL.  
  
## Sintaxis  
  
```  
  
      struct _AtlCreateWndData{  
   void* m_pThis;  
   DWORD m_dwThreadID;  
   _AtlCreateWndData* m_pNext;  
};  
```  
  
## Members  
 **m\_pThis**  
 El puntero de **this** utilizado para obtener acceso a la instancia de clase en procedimientos de ventana.  
  
 `m_dwThreadID`  
 El identificador de subproceso de la instancia de la clase actual.  
  
 **m\_pNext**  
 Puntero al siguiente objeto de `_AtlCreateWndData` .  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)