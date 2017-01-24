---
title: "CRBTree Class | Microsoft Docs"
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
  - "ATL.CRBTree"
  - "CRBTree"
  - "ATL::CRBTree"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBTree class"
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRBTree Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y utilizar un árbol de Rojo\-Negro.  
  
## Sintaxis  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBTree  
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
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](../Topic/CRBTree::KINARGTYPE.md)|Tipo utilizado cuando una tecla se pasa como argumento de entrada.|  
|[CRBTree::KOUTARGTYPE](../Topic/CRBTree::KOUTARGTYPE.md)|Tipo utilizado cuando una tecla se devuelve como argumento de salida.|  
|[CRBTree::VINARGTYPE](../Topic/CRBTree::VINARGTYPE.md)|Tipo utilizado cuando un valor se pasa como argumento de entrada.|  
|[CRBTree::VOUTARGTYPE](../Topic/CRBTree::VOUTARGTYPE.md)|Tipo utilizado cuando un valor se pasa como argumento de salida.|  
  
### Clases pública  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBTree::CPair Class](../Topic/CRBTree::CPair%20Class.md)|Una clase que contiene los elementos de clave y valor.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBTree::~CRBTree](../Topic/CRBTree::~CRBTree.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](../Topic/CRBTree::FindFirstKeyAfter.md)|Llame a este método para buscar la posición del elemento que utiliza la clave disponible siguiente.|  
|[CRBTree::GetAt](../Topic/CRBTree::GetAt.md)|Llame a este método para obtener el elemento en una posición determinada del árbol.|  
|[CRBTree::GetCount](../Topic/CRBTree::GetCount.md)|Llame a este método para obtener el número de elementos del árbol.|  
|[CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)|Llame a este método para obtener el valor de la posición del elemento en el administrador del árbol.|  
|[CRBTree::GetKeyAt](../Topic/CRBTree::GetKeyAt.md)|Llame a este método para obtener la clave de una posición determinada del árbol.|  
|[CRBTree::GetNext](../Topic/CRBTree::GetNext.md)|Llame a este método para obtener un puntero a un elemento almacenado en el objeto de `CRBTree` , y avanzar la posición al elemento siguiente.|  
|[CRBTree::GetNextAssoc](../Topic/CRBTree::GetNextAssoc.md)|Llame a este método para obtener la clave y el valor de un elemento del mapa y para avanzar la posición al elemento siguiente.|  
|[CRBTree::GetNextKey](../Topic/CRBTree::GetNextKey.md)|Llame a este método para obtener la clave de un elemento almacenado en el árbol y para avanzar la posición al elemento siguiente.|  
|[CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)|Llame a este método para obtener el valor de un elemento del árbol y para avanzar la posición al elemento siguiente.|  
|[CRBTree::GetPrev](../Topic/CRBTree::GetPrev.md)|Llame a este método para obtener un puntero a un elemento almacenado en el objeto de `CRBTree` , y después para actualizar la posición al elemento anterior.|  
|[CRBTree::GetTailPosition](../Topic/CRBTree::GetTailPosition.md)|Llame a este método para obtener el valor de la posición del elemento en la cola de árbol.|  
|[CRBTree::GetValueAt](../Topic/CRBTree::GetValueAt.md)|Llame a este método para recuperar el valor almacenado en una posición determinada del objeto de `CRBTree` .|  
|[CRBTree::IsEmpty](../Topic/CRBTree::IsEmpty.md)|Llame a este método para comprobar un objeto vacío de árbol.|  
|[CRBTree::RemoveAll](../Topic/CRBTree::RemoveAll.md)|Llame a este método para quitar todos los elementos del objeto de **CRBTree** .|  
|[CRBTree::RemoveAt](../Topic/CRBTree::RemoveAt.md)|Llame a este método para quitar el elemento en la posición especificada en el objeto de **CRBTree** .|  
|[CRBTree::SetValueAt](../Topic/CRBTree::SetValueAt.md)|Llame a este método para cambiar el valor almacenado en una posición determinada del objeto de `CRBTree` .|  
  
## Comentarios  
 Un árbol de Rojo\-Negro es un árbol de búsqueda binaria que utiliza un bit adicional de información por nodo para garantizar que sigue siendo “equilibrado”, es decir, el alto del árbol no crece desproporcionado grande y no afecta al rendimiento.  
  
 Esta clase de plantilla está diseñada para ser utilizada en [CRBMap](../../atl/reference/crbmap-class.md) y [CRBMultiMap](../../atl/reference/crbmultimap-class.md).  La mayor parte de los métodos que componen estas clases derivadas proporcionado por `CRBTree`.  
  
 Para obtener la descripción completa de las distintas clases de colección y de sus características y características de rendimiento, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)