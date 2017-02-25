---
title: "CRBMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CRBMap"
  - "CRBMap"
  - "ATL::CRBMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMap class"
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CRBMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa una estructura de asignación, utilizando un árbol binario de Rojo\-Negro.  
  
## Sintaxis  
  
```  
  
      template<   
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >   
> class CRBMap : public CRBTree< K, V, KTraits, VTraits >  
```  
  
#### Parámetros  
 `K`  
 el tipo de elemento clave.  
  
 *V*  
 El tipo de elemento del valor.  
  
 `KTraits`  
 El código utilizado para copiar o mover elementos clave.  Vea [clase de CElementTraits](../../atl/reference/celementtraits-class.md) para más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBMap::CRBMap](../Topic/CRBMap::CRBMap.md)|el constructor.|  
|[CRBMap::~CRBMap](../Topic/CRBMap::~CRBMap.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBMap::Lookup](../Topic/CRBMap::Lookup.md)|Llame a este método para buscar las claves o valores en el objeto de `CRBMap` .|  
|[CRBMap::RemoveKey](../Topic/CRBMap::RemoveKey.md)|Llame a este método para quitar un elemento de objeto de `CRBMap` , dada la clave.|  
|[CRBMap::SetAt](../Topic/CRBMap::SetAt.md)|Llame a este método para insertar un par de elementos del mapa.|  
  
## Comentarios  
 `CRBMap` proporciona compatibilidad para una matriz de asignación de tipo, controlando matriz ordenada de elementos clave y sus valores asociados.  Cada clave sólo puede tener un valor asociado.  Los elementos \(se compone de una clave y un valor\) se almacenan en una estructura de los árboles binario, utilizando el método de [CRBMap:: SetAt](../Topic/CRBMap::SetAt.md) .  Los elementos se pueden quitar mediante el método de [CRBMap:: RemoveKey](../Topic/CRBMap::RemoveKey.md) , lo que elimina el elemento con el valor de clave especificado.  
  
 Atravesar el árbol se crea posible con métodos como [CRBTree:: GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md), [CRBTree:: GetNext](../Topic/CRBTree::GetNext.md), y [CRBTree:: GetNextValue](../Topic/CRBTree::GetNextValue.md).  
  
 Los parámetros de `KTraits` y de `VTraits` son clases de con los que contienen cualquier código complementario necesario para copiar o mover elementos.  
  
 `CRBMap` es derivado de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo de Rojo\-Negro.  [CRBMultiMap](../../atl/reference/crbmultimap-class.md) es una variación que permite varios valores para cada clave.  También es derivada de `CRBTree`, por lo que de las acciones muchas características con `CRBMap`.  
  
 Una alternativa a los `CRBMap` y `CRBMultiMap` proporciona la clase de [CAtlMap](../../atl/reference/catlmap-class.md) .  Cuando solo una pequeña cantidad de elementos deben estar almacenados, considere la clase de [CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.  
  
 Para obtener la descripción completa de las distintas clases de colección y de sus características y características de rendimiento, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap Class](../../atl/reference/crbmultimap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)