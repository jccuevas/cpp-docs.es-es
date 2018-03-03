---
title: "Posición del elemento de Control de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db47e27ad0b556e08f51685bf84b6bd998722239
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-position"></a>Posición de los elementos del control de árbol
Posición inicial de un elemento se establece cuando el elemento se agrega al control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) mediante el uso de la `InsertItem` función miembro. La llamada de función miembro especifica el identificador del elemento primario y el identificador del elemento después del cual se va a insertar el nuevo elemento. El segundo identificador debe identificar un elemento secundario del primario dado o uno de estos valores: `TVI_FIRST`, `TVI_LAST`, o `TVI_SORT`.  
  
 Cuando `TVI_FIRST` o `TVI_LAST` se especifica, el control de árbol coloca el nuevo elemento al principio o al final de la lista del elemento primario determinado de elementos secundarios. Cuando `TVI_SORT` se especifica, el control de árbol inserta el nuevo elemento en la lista de elementos secundarios en orden alfabético según el texto de las etiquetas de elemento.  
  
 Puede colocar la lista de un elemento primario de los elementos secundarios en orden alfabético mediante una llamada a la [función miembro SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) función miembro. Esta función incluye un parámetro que especifica si todos los niveles de elementos secundarios descendiendo desde el elemento primario dado también se ordenan en orden alfabético.  
  
 El [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) función miembro le permite ordenar los elementos secundarios en función de criterios que se definan. Cuando se llama a esta función, se especifica una función de devolución de llamada definida por la aplicación que puede llamar el control de árbol siempre que es necesario decidir el orden relativo de dos elementos secundarios. La función de devolución de llamada recibe dos valores definidos por la aplicación de 32 bits para los elementos que se comparan y un tercer valor de 32 bits que especifica al llamar a `SortChildrenCB`.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

