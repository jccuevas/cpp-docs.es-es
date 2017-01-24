---
title: "CPtrList Class | Microsoft Docs"
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
  - "CPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPtrList class"
  - "generic lists"
  - "listas, generic"
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite listas de punteros void.  
  
## Sintaxis  
  
```  
class CPtrList : public CObject  
```  
  
## Miembros  
 Las funciones miembro de `CPtrList` son similares a las funciones miembro de la clase [CObList](../../mfc/reference/coblist-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro.  Siempre que vea un puntero `CObject` como un parámetro o un valor devuelto de función, utilice un puntero a `void`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 por ejemplo, se traduce en  
  
 `void*& CPtrList::GetHead() const;`  
  
## Comentarios  
 `CPtrList` incorpora la macro `IMPLEMENT_DYNAMIC` para admitir el acceso a tipos en tiempo de ejecución y el volcado en un objeto `CDumpContext`.  Si se necesita un volcado de elementos de lista de punteros individuales, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.  
  
 Las listas de punteros no se pueden serializar.  
  
 Cuando se elimina un objeto `CPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.  
  
 Para obtener más información sobre cómo utilizar `CPtrList`, vea el artículo [Colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## Requisitos  
 **Encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)