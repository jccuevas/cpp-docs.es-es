---
title: "CDefaultHashTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDefaultHashTraits"
  - "ATL.CDefaultHashTraits<T>"
  - "ATL::CDefaultHashTraits<T>"
  - "ATL.CDefaultHashTraits"
  - "ATL::CDefaultHashTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultHashTraits class"
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDefaultHashTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona una función estática por valores hash. calcular  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
>  
class CDefaultHashTraits  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](../Topic/CDefaultHashTraits::Hash.md)|\(Estático\) llame a esta función para calcular un valor hash para un elemento especificado.|  
  
## Comentarios  
 Esta clase contiene una única función estática que devuelve un valor hash para un elemento especificado.  esta clase es utilizada por [clase de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)