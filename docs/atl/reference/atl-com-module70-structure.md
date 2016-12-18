---
title: "_ATL_COM_MODULE70 Structure | Microsoft Docs"
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
  - "ATL::_ATL_COM_MODULE70"
  - "ATL._ATL_COM_MODULE70"
  - "_ATL_COM_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_COM_MODULE70 structure"
  - "ATL_COM_MODULE70 structure"
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_COM_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado por código COM\-relacionado en ATL.  
  
## Sintaxis  
  
```  
  
      struct _ATL_COM_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInstTypeLib;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;  
   CRITICAL_SECTION m_csObjMap;  
};  
```  
  
## Members  
 `cbSize`  
 El tamaño de la estructura, utilizado para la versión.  
  
 `m_hInstTypeLib`  
 La instancia del identificador de la biblioteca de tipos para este módulo.  
  
 **m\_ppAutoObjMapFirst**  
 La dirección del elemento de matriz que indica el principio del objeto asigna las entradas para este módulo.  
  
 **m\_ppAutoObjMapLast**  
 La dirección del elemento de matriz que indica el final del objeto asigna las entradas para este módulo.  
  
 `m_csObjMap`  
 La sección crítica para serializar el acceso al objeto asigna entradas.  Se utiliza internamente para ATL.  
  
## Comentarios  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md) se define como typedef de `_ATL_COM_MODULE70`.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)