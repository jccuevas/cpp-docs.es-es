---
title: "CElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CElementTraits<T>"
  - "ATL::CElementTraits"
  - "ATL.CElementTraits"
  - "ATL::CElementTraits<T>"
  - "CElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CElementTraits class"
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es utilizada por las clases de colección para proporcionar métodos y funciones para mover, copiar, la comparación, y aplicar un algoritmo hash operaciones.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
>  
class CElementTraits : public CDefaultElementTraits< T >  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Comentarios  
 Esta clase proporciona funciones estáticas predeterminadas y los métodos para mover, copiar, comparar, y aplicar un algoritmo hash a los elementos almacenados en un objeto de clase de colección.  `CElementTraits` es especificado como proveedor predeterminado de estas operaciones por las clases de colección [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), y [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Las implementaciones predeterminadas serán suficientes para los tipos de datos simples, pero si las clases de colección se utilizan para almacenar objetos más complejos, las funciones y los métodos deben reemplazar por implementaciones usuario\- proporcionadas.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)