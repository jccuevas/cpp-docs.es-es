---
title: "CComAutoDeleteCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAutoDeleteCriticalSection"
  - "CComAutoDeleteCriticalSection"
  - "ATL::CComAutoDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoDeleteCriticalSection class"
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CComAutoDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## Sintaxis  
  
```  
  
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection  
  
```  
  
## Comentarios  
 `CComAutoDeleteCriticalSection` deriva de la clase [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md).  Sin embargo, `CComAutoDeleteCriticalSection` invalida el método de [término](../Topic/CComSafeDeleteCriticalSection::Term.md) a acceso de `private` , que exige que la limpieza de memoria interna para producir cuando las instancias de esta clase salen del ámbito o explícitamente se eliminan de la memoria.  
  
 Esta clase no presenta ningún método adicional sobre su clase base.  Vea [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) y [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre clases auxiliares de sección crítica.  
  
## Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## Requisitos  
 **Header:** atlcore.h  
  
## Vea también  
 [CComSafeDeleteCriticalSection Class](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)