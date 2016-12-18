---
title: "CRBMultiMap Class | Microsoft Docs"
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
  - "CRBMultiMap"
  - "ATL.CRBMultiMap"
  - "ATL::CRBMultiMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMultiMap class"
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRBMultiMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa una estructura de asignación que permita cada tecla puede estar asociado a más de un valor, utilizando un árbol binario de Rojo\-Negro.  
  
## Sintaxis  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBMultiMap : public CRBTree< K, V, KTraits, VTraits >  
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
|[CRBMultiMap::CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md)|el constructor.|  
|[CRBMultiMap::~CRBMultiMap](../Topic/CRBMultiMap::~CRBMultiMap.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md)|Llame a este método para buscar la posición del primer elemento con una clave especificada.|  
|[CRBMultiMap::GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md)|Llame a este método para obtener el valor asociado con una clave especificada, y actualizar el valor de la posición.|  
|[CRBMultiMap::GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md)|Llame a este método para obtener el elemento asociado con una clave especificada, y actualizar el valor de la posición.|  
|[CRBMultiMap::Insert](../Topic/CRBMultiMap::Insert.md)|Llame a este método para insertar un par de elementos del mapa.|  
|[CRBMultiMap::RemoveKey](../Topic/CRBMultiMap::RemoveKey.md)|Llame a este método para quitar todos los elementos de clave y valor para una clave especificada.|  
  
## Comentarios  
 `CRBMultiMap` proporciona compatibilidad para una matriz de asignación de tipo, controlando matriz ordenada de elementos clave y valores.  A diferencia de la clase de [CRBMap](../../atl/reference/crbmap-class.md) , cada clave puede estar asociado a más de un valor.  
  
 Los elementos \(se compone de una clave y un valor\) se almacenan en una estructura de los árboles binario, utilizando el método de [CRBMultiMap:: Insert](../Topic/CRBMultiMap::Insert.md) .  Los elementos se pueden quitar mediante el método de [CRBMultiMap:: RemoveKey](../Topic/CRBMultiMap::RemoveKey.md) , lo que elimina todos los elementos que coinciden con la clave especificada.  
  
 Atravesar el árbol se crea posible con métodos como [CRBTree:: GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md), [CRBTree:: GetNext](../Topic/CRBTree::GetNext.md), y [CRBTree:: GetNextValue](../Topic/CRBTree::GetNextValue.md).  El acceso de los valores potencialmente varias por clave es posible mediante los métodos de [CRBMultiMap:: FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md), de [CRBMultiMap:: GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md), y de [CRBMultiMap:: GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md) .  Vea el ejemplo para [CRBMultiMap:: CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md) para obtener un ejemplo de esto en el laboratorio.  
  
 Los parámetros de `KTraits` y de `VTraits` son clases de con los que contienen cualquier código complementario necesario para copiar o mover elementos.  
  
 `CRBMultiMap` es derivado de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo de Rojo\-Negro.  Una alternativa a `CRBMultiMap` y a `CRBMap` proporciona la clase de [CAtlMap](../../atl/reference/catlmap-class.md) .  Cuando solo una pequeña cantidad de elementos deben estar almacenados, considere la clase de [CSimpleMap](../../atl/reference/csimplemap-class.md) en su lugar.  
  
 Para obtener la descripción completa de las distintas clases de colección y de sus características y características de rendimiento, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMap Class](../../atl/reference/crbmap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)