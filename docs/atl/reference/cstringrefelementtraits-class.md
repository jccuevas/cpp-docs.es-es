---
title: "CStringRefElementTraits Class | Microsoft Docs"
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
  - "CStringRefElementTraits"
  - "ATL.CStringRefElementTraits"
  - "ATL::CStringRefElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringRefElementTraits class"
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringRefElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona las funciones estáticas relacionadas con cadenas almacenadas en objetos de clase de colección.  los objetos string se tratan de como referencias.  
  
## Sintaxis  
  
```  
  
      template<   
   typename T  
>  
class CStringRefElementTraits : public CElementTraitsBase< T >  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](../Topic/CStringRefElementTraits::CompareElements.md)|Llame a esta función estática para comparar dos elementos string para la igualdad.|  
|[CStringRefElementTraits::CompareElementsOrdered](../Topic/CStringRefElementTraits::CompareElementsOrdered.md)|Llame a esta función estática para comparar dos elementos string.|  
|[CStringRefElementTraits::Hash](../Topic/CStringRefElementTraits::Hash.md)|Llame a esta función estática para calcular un valor hash para el elemento especificado de la cadena.|  
  
## Comentarios  
 Esta clase proporciona las funciones estáticas para comparar cadenas y para crear un valor hash.  Estas funciones son útiles al utilizar una clase de colección para almacenar cadena\-basó datos.  A[diferencia de CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) y[de CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md),`CStringRefElementTraits` hace que`CString` los argumentos que se deben pasar como **const CString&** hace referencia.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)