---
title: "CAtlList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlList"
  - "CAtlList"
  - "ATL::CAtlList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlList class"
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y administrar un objeto list.  
  
## Sintaxis  
  
```  
  
      template<  
   typename E,  
   class ETraits = CElementTraits< E >  
>  
class CAtlList  
```  
  
#### Parámetros  
 `E`  
 Tipo del elemento.  
  
 `ETraits`  
 El código utilizado para copiar o mover elementos.  Vea [clase de CElementTraits](../../atl/reference/celementtraits-class.md) para más detalles.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](../Topic/CAtlList::INARGTYPE.md)||  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlList::CAtlList](../Topic/CAtlList::CAtlList.md)|el constructor.|  
|[CAtlList::~CAtlList](../Topic/CAtlList::~CAtlList.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlList::AddHead](../Topic/CAtlList::AddHead.md)|Llame a este método para agregar un elemento al principio de la lista.|  
|[CAtlList::AddHeadList](../Topic/CAtlList::AddHeadList.md)|Llame a este método para agregar una lista existente al encabezado de la lista.|  
|[CAtlList::AddTail](../Topic/CAtlList::AddTail.md)|Llame a este método para agregar un elemento a la cola de esta lista.|  
|[CAtlList::AddTailList](../Topic/CAtlList::AddTailList.md)|Llame a este método para agregar una lista existente en la cola de esta lista.|  
|[CAtlList::AssertValid](../Topic/CAtlList::AssertValid.md)|Llame a este método para confirmar la lista es válido.|  
|[CAtlList::Find](../Topic/CAtlList::Find.md)|Llame a este método para buscar la lista para el elemento especificado.|  
|[CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md)|Llame a este método para obtener la posición de un elemento, proporcionando un valor de índice.|  
|[CAtlList::GetAt](../Topic/CAtlList::GetAt.md)|Llame a este método para devolver el elemento en una posición especificada en la lista.|  
|[CAtlList::GetCount](../Topic/CAtlList::GetCount.md)|Llame a este método para devolver el número de objetos de la lista.|  
|[CAtlList::GetHead](../Topic/CAtlList::GetHead.md)|Llame a este método para devolver el elemento en el encabezado de la lista.|  
|[CAtlList::GetHeadPosition](../Topic/CAtlList::GetHeadPosition.md)|Llame a este método para obtener la posición del encabezado de la lista.|  
|[CAtlList::GetNext](../Topic/CAtlList::GetNext.md)|Llame a este método para devolver el siguiente elemento de la lista.|  
|[CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md)|Llame a este método para devolver el elemento anterior de la lista.|  
|[CAtlList::GetTail](../Topic/CAtlList::GetTail.md)|Llame a este método para devolver el elemento en la cola de la lista.|  
|[CAtlList::GetTailPosition](../Topic/CAtlList::GetTailPosition.md)|Llame a este método para obtener la posición de la cola de la lista.|  
|[CAtlList::InsertAfter](../Topic/CAtlList::InsertAfter.md)|Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.|  
|[CAtlList::InsertBefore](../Topic/CAtlList::InsertBefore.md)|Llame a este método para insertar un nuevo elemento en la lista antes de la posición especificada.|  
|[CAtlList::IsEmpty](../Topic/CAtlList::IsEmpty.md)|Llame a este método para determinar si la lista está vacía.|  
|[CAtlList::MoveToHead](../Topic/CAtlList::MoveToHead.md)|Llame a este método para mover el elemento especificado al principio de la lista.|  
|[CAtlList::MoveToTail](../Topic/CAtlList::MoveToTail.md)|Llame a este método para mover el elemento especificado a la cola de la lista.|  
|[CAtlList::RemoveAll](../Topic/CAtlList::RemoveAll.md)|Llame a este método para quitar todos los elementos de la lista.|  
|[CAtlList::RemoveAt](../Topic/CAtlList::RemoveAt.md)|Llame a este método para quitar un solo elemento de la lista.|  
|[CAtlList::RemoveHead](../Topic/CAtlList::RemoveHead.md)|Llame a este método para quitar el elemento en el encabezado de la lista.|  
|[CAtlList::RemoveHeadNoReturn](../Topic/CAtlList::RemoveHeadNoReturn.md)|Llame a este método para quitar el elemento en el encabezado de la lista sin devolver ningún valor.|  
|[CAtlList::RemoveTail](../Topic/CAtlList::RemoveTail.md)|Llame a este método para quitar el elemento en la cola de la lista.|  
|[CAtlList::RemoveTailNoReturn](../Topic/CAtlList::RemoveTailNoReturn.md)|Llame a este método para quitar el elemento en la cola de la lista sin devolver ningún valor.|  
|[CAtlList::SetAt](../Topic/CAtlList::SetAt.md)|Llame a este método para establecer el valor del elemento en una posición determinada de la lista.|  
|[CAtlList::SwapElements](../Topic/CAtlList::SwapElements.md)|Llame a este método para cambiar elementos de la lista.|  
  
## Comentarios  
 La de la clase de `CAtlList` pidieron listas de objetos nonunique accesibles secuencialmente o por valor.  Las listas de`CAtlList` se comportan como listas doblemente vinculadas.  Cada lista tiene un encabezado y una cola, y los nuevos elementos \(o listas en algunos casos\) se pueden agregar al final de la lista, o insertar antes o después de elementos concretos.  
  
 La mayoría de los métodos de `CAtlList` hace uso de un valor de posición.  Este valor lo utilizan los métodos para hacer referencia a la ubicación de memoria real donde se almacenan los elementos, y no se debe calcular o predecir directamente.  Si es necesario tener acceso al *enésimo*elemento en la lista, el método [CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md) devolverá el valor correspondiente de la posición del índice especificado.  Los métodos [CAtlList::GetNext](../Topic/CAtlList::GetNext.md) y [CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md) se pueden utilizar para recorrer en iteración los objetos de la lista.  
  
 Para obtener más información sobre los tipos de colecciones disponibles con ATL, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CList Class](../../mfc/reference/clist-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)