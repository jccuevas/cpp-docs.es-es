---
title: "CComQIPtrElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComQIPtrElementTraits"
  - "CComQIPtrElementTraits"
  - "ATL::CComQIPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtrElementTraits class"
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComQIPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos, funciones estáticas, y tipos útiles al crear colecciones de punteros de interfaz COM.  
  
## Sintaxis  
  
```  
  
      template<  
   typename I,  
   const IID* piid = & __uuidof( I )   
>   
class CComQIPtrElementTraits : public CDefaultElementTraits<  
   ATL::CComQIPtr< I, piid >  
>  
```  
  
#### Parámetros  
 `I`  
 Una interfaz COM que especifica el tipo de puntero que se va a almacenar.  
  
 `piid`  
 Un puntero al identificador IID de `I`.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](../Topic/CComQIPtrElementTraits::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
  
## Comentarios  
 Esta clase se deriva métodos y proporciona una definición útil al crear una clase de colección de objetos de puntero de interfaz COM de [CComQIPtr](../../atl/reference/ccomqiptr-class.md) .  esta clase es utilizada por las clases de [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) y de [CInterfaceList](../../atl/reference/cinterfacelist-class.md) .  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)