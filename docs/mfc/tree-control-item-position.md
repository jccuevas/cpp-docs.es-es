---
title: "Posici&#243;n de los elementos del control de &#225;rbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl (clase), posición del elemento"
  - "posición del elemento en controles de árbol"
  - "posición, CTreeCtrl (elementos)"
  - "controles de árbol, posición del elemento"
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Posici&#243;n de los elementos del control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se establece la posición inicial de un elemento cuando el elemento se agrega al control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) utilizando la función miembro de `InsertItem` .  La llamada de función miembro especifica el identificador del elemento primario y el identificador del elemento tras el que el nuevo elemento se va a insertar.  El segundo identificador debe identificar un elemento secundario del elemento primario especificado o uno de estos valores: `TVI_FIRST`, `TVI_LAST`, o `TVI_SORT`.  
  
 Cuando se especifica `TVI_FIRST` o `TVI_LAST` , el control de árbol coloca el nuevo elemento al principio o el final de la lista del elemento primario especificado de elementos secundarios.  Cuando se especifica `TVI_SORT` , el control de árbol inserta el nuevo elemento en la lista de elementos secundarios ordenados alfabéticamente por en el texto de las etiquetas del elemento.  
  
 Puede colocar la lista de un elemento primario de elementos secundarios en orden alfabético llamando a la función miembro de [SortChildren](../Topic/CTreeCtrl::SortChildren.md) .  Esta función incluye un parámetro que especifica si todos los niveles de elementos secundarios que descienden del elemento primario especificado también están ordenados en orden alfabético.  
  
 La función miembro de [SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md) permite ordenar los elementos secundarios basándose en los criterios que se define.  Cuando se llama a esta función, puede especificar una función de devolución de llamada definido por la aplicación que el control de árbol puede llamar siempre que el orden relativo de dos elementos secundarios necesita ser decidido.  La función de devolución de llamada recibe dos valores definidos por la aplicación de 32 bits para los elementos comparados y un tercer valor de 32 bits que se especifica al llamar a `SortChildrenCB`.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)