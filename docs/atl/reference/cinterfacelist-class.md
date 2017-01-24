---
title: "CInterfaceList Class | Microsoft Docs"
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
  - "ATL::CInterfaceList"
  - "ATL.CInterfaceList"
  - "CInterfaceList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterfaceList class"
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterfaceList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos útiles al crear una lista de punteros de interfaz COM.  
  
## Sintaxis  
  
```  
  
      template<  
   class I,  
   const IID* piid = & __uuidof( I )  
>   
class CInterfaceList : public CAtlList<  
   ATL::CComQIPtr< I, piid >,  
   CComQIPtrElementTraits< I, piid >  
>  
```  
  
#### Parámetros  
 `I`  
 Una interfaz COM que especifica el tipo de puntero que se va a almacenar.  
  
 `piid`  
 Un puntero al identificador IID de `I`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](../Topic/CInterfaceList::CInterfaceList.md)|El constructor de la lista de interfaces.|  
  
## Comentarios  
 Esta clase proporciona un constructor y métodos derivados para crear una lista de punteros de interfaz COM.  Uso [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiere una matriz.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CComQIPtr Class](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)