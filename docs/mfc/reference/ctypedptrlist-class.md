---
title: "CTypedPtrList Class | Microsoft Docs"
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
  - "CTypedPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrList class"
  - "linked lists [C++]"
  - "lists [C++]"
  - "pointer lists"
  - "template classes, CTypedPtrList class"
  - "type-safe collections"
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTypedPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona un “contenedor seguro” para los objetos de la clase `CPtrList`.  
  
## Sintaxis  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### Parámetros  
 `BASE_CLASS`  
 Clase base del tipo de clase de la lista de puntero; debe ser una clase de la lista de puntero \(`CObList` o `CPtrList`\).  
  
 `TYPE`  
 Tipo de los elementos almacenados en la lista de clases base.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](../Topic/CTypedPtrList::AddHead.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) al principio de la lista \(crea un nuevo encabezado\).|  
|[CTypedPtrList::AddTail](../Topic/CTypedPtrList::AddTail.md)|Agrega un elemento \(o todos los elementos de otros enumerados\) a la cola de la lista \(crea una nueva cola\).|  
|[CTypedPtrList::GetAt](../Topic/CTypedPtrList::GetAt.md)|Obtiene el elemento en una posición determinada.|  
|[CTypedPtrList::GetHead](../Topic/CTypedPtrList::GetHead.md)|Devuelve el elemento principal de la lista \(no puede estar vacía\).|  
|[CTypedPtrList::GetNext](../Topic/CTypedPtrList::GetNext.md)|Obtiene el elemento siguiente para recorrer.|  
|[CTypedPtrList::GetPrev](../Topic/CTypedPtrList::GetPrev.md)|Obtiene el elemento anterior para recorrer.|  
|[CTypedPtrList::GetTail](../Topic/CTypedPtrList::GetTail.md)|Devuelve el elemento de cola de la lista \(no puede estar vacía\).|  
|[CTypedPtrList::RemoveHead](../Topic/CTypedPtrList::RemoveHead.md)|Quita el elemento del encabezado de la lista.|  
|[CTypedPtrList::RemoveTail](../Topic/CTypedPtrList::RemoveTail.md)|Quita el elemento de cola de la lista.|  
|[CTypedPtrList::SetAt](../Topic/CTypedPtrList::SetAt.md)|Establece el elemento en una posición determinada.|  
  
## Comentarios  
 Cuando se utiliza `CTypedPtrList` en lugar de `CObList` o `CPtrList`, ayuda a facilitar la comprobación de tipos de C\+\+ eliminan los errores producidos por los tipos de puntero no coincidentes.  
  
 Además, el contenedor de `CTypedPtrList` realiza muchos del marco que es obligatorio si utilizó `CObList` o `CPtrList`.  
  
 Dado que todas las funciones de `CTypedPtrList` inline, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Las listas derivadas de `CObList` pueden serializar, pero las derivadas de `CPtrList` no pueden.  
  
 Cuando se elimina un objeto de `CTypedPtrList` , o cuando se quitan los elementos, solo se quitan los punteros, no las entidades que hacen referencia.  
  
 Para obtener más información sobre cómo utilizar `CTypedPtrList`, vea los artículos [colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## Ejemplo  
 Este ejemplo crea una instancia de `CTypedPtrList`, agregue un objeto, serializa la lista en el disco, y se elimina el objeto:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/CPP/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/CPP/ctypedptrlist-class_2.cpp)]  
  
## Jerarquía de herencia  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## Requisitos  
 **encabezado:** afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)