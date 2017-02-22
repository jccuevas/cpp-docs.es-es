---
title: "_ATL_WIN_MODULE70 Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_WIN_MODULE70"
  - "ATL::_ATL_WIN_MODULE70"
  - "ATL._ATL_WIN_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_WIN_MODULE70 structure"
  - "ATL_WIN_MODULE70 structure"
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# _ATL_WIN_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado por código de visualización en una ventana de ATL.  
  
## Sintaxis  
  
```  
  
      struct _ATL_WIN_MODULE70{  
   UNIT cbSize;  
   CRITICAL_SECTION m_csWindowCreate;  
   _AtlCreateWndData* m_pCreateWndList;  
   CSimpleArray<ATOM> m_rgWindowClassAtoms;  
};  
```  
  
## Members  
 `cbSize`  
 El tamaño de la estructura, utilizado para la versión.  
  
 `m_csWindowCreate`  
 Se utiliza para serializar el acceso al código de registro de la ventana.  Se utiliza internamente para ATL.  
  
 **m\_pCreateWndList**  
 Se utiliza para enlazar las ventanas en sus objetos.  Se utiliza internamente para ATL.  
  
 **m\_rgWindowClassAtoms**  
 Se utilizan para realizar el seguimiento de los registros de la clase de ventana para que puedan ser correctamente no registrados en la finalización.  Se utiliza internamente para ATL.  
  
## Comentarios  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md) se define como typedef de `_ATL_WIN_MODULE70`.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)