---
title: "CStringList Class | Microsoft Docs"
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
  - "CStringList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringList class"
  - "listas, cadena"
  - "cadenas [C++], colecciones"
  - "cadenas [C++], listas"
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

admite listas de objetos de `CString` .  
  
## Sintaxis  
  
```  
class CStringList : public CObject  
```  
  
## Miembros  
 Las funciones miembro de `CStringList` son similares a las funciones miembro de clases [CObList](../../mfc/reference/coblist-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como valor devuelto, sustituya `CString` \(no un puntero de `CString` \).  Siempre que aparezca un puntero de `CObject` como parámetro de la función, sustituya `LPCTSTR`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 por ejemplo, convierte a  
  
 `CString& CStringList::GetHead() const;`  
  
 y  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 convierte a  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|Crea una lista vacía.|  
  
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
 Todas las comparaciones son realizadas por valor, lo que significa que los caracteres de la cadena se comparan en lugar de las direcciones de las cadenas.  
  
 `CStringList` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Si una lista de objetos de `CString` se almacena en un archivo, con un operador sobrecargado de inserción o con la función miembro de `Serialize` , cada elemento de `CString` se serializa en su lugar.  
  
 Si necesita un volcado de memoria de los elementos individuales de `CString` , debe establecer el nivel de contexto de volcado de memoria en 1 o posterior.  
  
 Para obtener más información sobre cómo utilizar `CStringList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)