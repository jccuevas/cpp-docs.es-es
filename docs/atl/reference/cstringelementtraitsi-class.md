---
title: "CStringElementTraitsI Class | Microsoft Docs"
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
  - "ATL::CStringElementTraitsI"
  - "CStringElementTraitsI"
  - "ATL.CStringElementTraitsI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraitsI class"
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringElementTraitsI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona las funciones estáticas relacionadas con cadenas almacenadas en objetos de clase de colección.  Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones sin distinción entre mayúsculas y minúsculas.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T,  
   class CharTraits = CDefaultCharTraits< T::XCHAR >  
>  
class CStringElementTraitsI : public CElementTraitsBase< T >  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](../Topic/CStringElementTraitsI::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
|[CStringElementTraitsI::OUTARGTYPE](../Topic/CStringElementTraitsI::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de objeto de la clase de colección.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](../Topic/CStringElementTraitsI::CompareElements.md)|Llame a esta función estática para comparar dos elementos string para la igualdad, omitiendo diferencias en caso de que.|  
|[CStringElementTraitsI::CompareElementsOrdered](../Topic/CStringElementTraitsI::CompareElementsOrdered.md)|Llame a esta función estática para comparar dos elementos string, omitiendo diferencias en caso de que.|  
|[CStringElementTraitsI::Hash](../Topic/CStringElementTraitsI::Hash.md)|Llame a esta función estática para calcular un valor hash para el elemento especificado de la cadena.|  
  
## Comentarios  
 Esta clase proporciona las funciones estáticas para comparar cadenas y para crear un valor hash.  Estas funciones son útiles al utilizar una clase de colección para almacenar cadena\-basó datos.  Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena son estar con tratará de como referencias.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CStringElementTraits Class](../../atl/reference/cstringelementtraits-class.md)