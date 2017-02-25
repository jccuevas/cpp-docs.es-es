---
title: "CAutoPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoPtrList"
  - "CAutoPtrList"
  - "ATL.CAutoPtrList"
  - "ATL::CAutoPtrList<E>"
  - "ATL.CAutoPtrList<E>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtrList class"
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAutoPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos útiles al crear una lista de punteros inteligentes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename E  
>  
class CAutoPtrList : public CAtlList<  
ATL::CAutoPtr< E>,  
CAutoPtrElementTraits< E>  
>  
```  
  
#### Parámetros  
 `E`  
 el tipo de puntero.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](../Topic/CAutoPtrList::CAutoPtrList.md)|el constructor.|  
  
## Comentarios  
 Esta clase proporciona un constructor y deriva métodos de [CAtlList](../../atl/reference/catllist-class.md) y de [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para facilitar la creación de un objeto de lista que almacena punteros inteligentes.  La clase [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) proporciona una función similar para un objeto array.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits Class](../../atl/reference/cautoptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)