---
title: "CAutoVectorPtrElementTraits Class | Microsoft Docs"
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
  - "ATL::CAutoVectorPtrElementTraits<T>"
  - "ATL.CAutoVectorPtrElementTraits"
  - "ATL.CAutoVectorPtrElementTraits<T>"
  - "ATL::CAutoVectorPtrElementTraits"
  - "CAutoVectorPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoVectorPtrElementTraits class"
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoVectorPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos, funciones estáticas, y tipos útiles al crear colecciones de punteros inteligentes utilizando el vector nuevo y operadores de cancelación.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename T  
>  
class CAutoVectorPtrElementTraits : public CDefaultElementTraits<  
ATL::CAutoVectorPtr< T>  
>  
```  
  
#### Parámetros  
 `T`  
 el tipo de puntero.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoVectorPtrElementTraits::INARGTYPE](../Topic/CAutoVectorPtrElementTraits::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](../Topic/CAutoVectorPtrElementTraits::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de objeto de la clase de colección.|  
  
## Comentarios  
 Esta clase proporciona métodos, funciones estáticas, y tipos para facilitar la creación de objetos de clase de colección que contienen punteros inteligentes.  A diferencia de [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), esta clase utiliza vector nuevo y elimina operadores.  
  
## Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [CAutoVectorPtr Class](../../atl/reference/cautovectorptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)