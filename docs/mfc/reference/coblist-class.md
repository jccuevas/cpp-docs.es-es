---
title: "CObList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CObList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObList class"
  - "listas, objeto"
  - "objetos [C++], lists of"
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CObList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite listas ordenadas de punteros nonunique de `CObject` accesibles secuencialmente o por valor de puntero.  
  
## Sintaxis  
  
```  
class CObList : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|Crea una lista vacía para punteros de `CObject` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::AddHead](../Topic/CObList::AddHead.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) al principio de la lista \(crea un nuevo encabezado\).|  
|[CObList::AddTail](../Topic/CObList::AddTail.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) a la cola de la lista \(crea una nueva cola\).|  
|[CObList::Find](../Topic/CObList::Find.md)|Obtiene la posición de un elemento especificado por valor de puntero.|  
|[CObList::FindIndex](../Topic/CObList::FindIndex.md)|Obtiene la posición de un elemento especificado por un índice de base cero.|  
|[CObList::GetAt](../Topic/CObList::GetAt.md)|Obtiene el elemento en una posición determinada.|  
|[CObList::GetCount](../Topic/CObList::GetCount.md)|devuelve el número de elementos en esta lista.|  
|[CObList::GetHead](../Topic/CObList::GetHead.md)|Devuelve el elemento principal de la lista \(no puede estar vacía\).|  
|[CObList::GetHeadPosition](../Topic/CObList::GetHeadPosition.md)|Devuelve la posición del elemento head de la lista.|  
|[CObList::GetNext](../Topic/CObList::GetNext.md)|Obtiene el elemento siguiente para recorrer.|  
|[CObList::GetPrev](../Topic/CObList::GetPrev.md)|Obtiene el elemento anterior para recorrer.|  
|[CObList::GetSize](../Topic/CObList::GetSize.md)|devuelve el número de elementos en esta lista.|  
|[CObList::GetTail](../Topic/CObList::GetTail.md)|Devuelve el elemento de cola de la lista \(no puede estar vacía\).|  
|[CObList::GetTailPosition](../Topic/CObList::GetTailPosition.md)|Devuelve la posición del elemento de cola de la lista.|  
|[CObList::InsertAfter](../Topic/CObList::InsertAfter.md)|Inserta un nuevo elemento después de una posición determinada.|  
|[CObList::InsertBefore](../Topic/CObList::InsertBefore.md)|Inserta un nuevo elemento antes de una posición determinada.|  
|[CObList::IsEmpty](../Topic/CObList::IsEmpty.md)|Comprueba la condición vacía de lista \(ningún elemento\).|  
|[CObList::RemoveAll](../Topic/CObList::RemoveAll.md)|quita todos los elementos de esta lista.|  
|[CObList::RemoveAt](../Topic/CObList::RemoveAt.md)|Quita un elemento de esta lista, especificada por posición.|  
|[CObList::RemoveHead](../Topic/CObList::RemoveHead.md)|Quita el elemento del encabezado de la lista.|  
|[CObList::RemoveTail](../Topic/CObList::RemoveTail.md)|Quita el elemento de cola de la lista.|  
|[CObList::SetAt](../Topic/CObList::SetAt.md)|Establece el elemento en una posición determinada.|  
  
## Comentarios  
 las listas de`CObList` se comportan como listas doble\-vinculadas.  
  
 Una variable de **POSICIÓN** con tipo es una clave de la lista.  Puede utilizar una variable de **POSICIÓN** como iterador para recorrer una lista secuencialmente y como marcador para contener un lugar.  Una posición no es igual que un índice, sin embargo.  
  
 La inserción de elementos es muy rápidamente al principio de la lista, en la cola, y en **POSICIÓN**conocido.  Una búsqueda secuencial es necesaria para buscar un elemento por valor o por índice.  esta búsqueda puede ser lenta si la lista es larga.  
  
 `CObList` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Si una lista de punteros de `CObject` se almacena en un archivo, con un operador sobrecargado de inserción o con la función miembro de `Serialize` , cada elemento de `CObject` es serializado a su vez.  
  
 Si necesita un volcado de elementos individuales de `CObject` en la lista, debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Cuando se elimina un objeto de `CObList` , o cuando se quitan los elementos, solo se quitan los punteros de `CObject` , no objetos que hacen referencia.  
  
 Puede derivar dispone de clases de `CObList`.  La nueva clase de lista, diseñada para contener punteros a objetos derivados de `CObject`, agrega nuevos miembros de datos y el nuevo miembro funciona.  Observe que la lista resultante no es seguro estrictamente tipo, porque permite la inserción de cualquier puntero de `CObject` .  
  
> [!NOTE]
>  Debe utilizar la macro de [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) en la implementación de la clase derivada si desea serializar la lista.  
  
 Para obtener más información sobre cómo utilizar `CObList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CStringList Class](../../mfc/reference/cstringlist-class.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)