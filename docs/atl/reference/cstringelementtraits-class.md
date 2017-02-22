---
title: "CStringElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CStringElementTraits<T>"
  - "ATL::CStringElementTraits<T>"
  - "CStringElementTraits"
  - "ATL.CStringElementTraits"
  - "ATL::CStringElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraits class"
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CStringElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona funciones estáticas que las clases de colección que almacenan los objetos de `CString` .  
  
## Sintaxis  
  
```  
  
      template<  
   typename T   
>  
class CStringElementTraits  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](../Topic/CStringElementTraits::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
|[CStringElementTraits::OUTARGTYPE](../Topic/CStringElementTraits::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de objeto de la clase de colección.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](../Topic/CStringElementTraits::CompareElements.md)|\(Estático\) llame a esta función para comparar dos elementos string para la igualdad.|  
|[CStringElementTraits::CompareElementsOrdered](../Topic/CStringElementTraits::CompareElementsOrdered.md)|\(Estático\) llame a esta función para comparar dos elementos string.|  
|[CStringElementTraits::CopyElements](../Topic/CStringElementTraits::CopyElements.md)|\(Estático\) llame a esta función para copiar los elementos de `CString` almacenados en un objeto de clase de colección.|  
|[CStringElementTraits::Hash](../Topic/CStringElementTraits::Hash.md)|\(Estático\) llame a esta función para calcular un valor hash para el elemento especificado de la cadena.|  
|[CStringElementTraits::RelocateElements](../Topic/CStringElementTraits::RelocateElements.md)|\(Estático\) llame a esta función para reubicar los elementos de `CString` almacenados en un objeto de clase de colección.|  
  
## Comentarios  
 Esta clase proporciona las funciones estáticas para copiar, mover, y comparar cadenas y para crear un valor hash.  Estas funciones son útiles al utilizar una clase de colección para almacenar cadena\-basó datos.  uso [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) cuando se requieren las comparaciones sin distinción entre mayúsculas y minúsculas.  Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena deben tratar de como referencias.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** cstringt.h  
  
## Vea también  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI Class](../../atl/reference/cstringelementtraitsi-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)