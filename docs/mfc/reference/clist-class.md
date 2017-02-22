---
title: "CList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CList class"
  - "listas"
  - "listas, base class for"
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite listas ordenadas de objetos nonunique accesibles secuencialmente o por valor.  
  
## Sintaxis  
  
```  
template< class TYPE, class ARG_TYPE = const TYPE& >   
class CList : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CList::CList](../Topic/CList::CList.md)|Crea una lista ordenada vacía.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CList::AddHead](../Topic/CList::AddHead.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) al principio de la lista \(crea un nuevo encabezado\).|  
|[CList::AddTail](../Topic/CList::AddTail.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) a la cola de la lista \(crea una nueva cola\).|  
|[CList::Find](../Topic/CList::Find.md)|Obtiene la posición de un elemento especificado por valor de puntero.|  
|[CList::FindIndex](../Topic/CList::FindIndex.md)|Obtiene la posición de un elemento especificado por un índice de base cero.|  
|[CList::GetAt](../Topic/CList::GetAt.md)|Obtiene el elemento en una posición determinada.|  
|[CList::GetCount](../Topic/CList::GetCount.md)|devuelve el número de elementos en esta lista.|  
|[CList::GetHead](../Topic/CList::GetHead.md)|Devuelve el elemento principal de la lista \(no puede estar vacía\).|  
|[CList::GetHeadPosition](../Topic/CList::GetHeadPosition.md)|Devuelve la posición del elemento head de la lista.|  
|[CList::GetNext](../Topic/CList::GetNext.md)|Obtiene el elemento siguiente para recorrer.|  
|[CList::GetPrev](../Topic/CList::GetPrev.md)|Obtiene el elemento anterior para recorrer.|  
|[CList::GetSize](../Topic/CList::GetSize.md)|devuelve el número de elementos en esta lista.|  
|[CList::GetTail](../Topic/CList::GetTail.md)|Devuelve el elemento de cola de la lista \(no puede estar vacía\).|  
|[CList::GetTailPosition](../Topic/CList::GetTailPosition.md)|Devuelve la posición del elemento de cola de la lista.|  
|[CList::InsertAfter](../Topic/CList::InsertAfter.md)|Inserta un nuevo elemento después de una posición determinada.|  
|[CList::InsertBefore](../Topic/CList::InsertBefore.md)|Inserta un nuevo elemento antes de una posición determinada.|  
|[CList::IsEmpty](../Topic/CList::IsEmpty.md)|Comprueba la condición vacía de lista \(ningún elemento\).|  
|[CList::RemoveAll](../Topic/CList::RemoveAll.md)|quita todos los elementos de esta lista.|  
|[CList::RemoveAt](../Topic/CList::RemoveAt.md)|Quita un elemento de esta lista, especificada por posición.|  
|[CList::RemoveHead](../Topic/CList::RemoveHead.md)|Quita el elemento del encabezado de la lista.|  
|[CList::RemoveTail](../Topic/CList::RemoveTail.md)|Quita el elemento de cola de la lista.|  
|[CList::SetAt](../Topic/CList::SetAt.md)|Establece el elemento en una posición determinada.|  
  
#### Parámetros  
 `TYPE`  
 tipo de objeto almacenado en la lista.  
  
 `ARG` *\_* `TYPE`  
 Tipo utilizado para hacer referencia a los objetos en la lista.  puede ser una referencia.  
  
## Comentarios  
 las listas de`CList` se comportan como listas doble\-vinculadas.  
  
 Una variable de **POSICIÓN** con tipo es una clave de la lista.  Puede utilizar una variable de **POSICIÓN** como iterador para recorrer una lista secuencialmente y como marcador para contener un lugar.  Una posición no es igual que un índice, sin embargo.  
  
 La inserción de elementos es muy rápidamente al principio de la lista, en la cola, y en **POSICIÓN**conocido.  Una búsqueda secuencial es necesaria para buscar un elemento por valor o por índice.  esta búsqueda puede ser lenta si la lista es larga.  
  
 Si necesita un volcado de elementos individuales en la lista, debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Algunas funciones miembro de las funciones globales de esta de la clase auxiliar de llamada que se deben personalizar para la mayoría de utilizan la clase de `CList` .  Vea [aplicaciones auxiliares de la clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección “las macros y Globals”.  
  
 Para obtener más información sobre cómo utilizar `CList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Ejemplo  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/CPP/clist-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## Requisitos  
 **encabezado:** afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)