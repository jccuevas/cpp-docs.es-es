---
title: "Elementos primario y secundario del control de &#225;rbol | Microsoft Docs"
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
  - "elementos secundarios de control de árbol"
  - "CTreeCtrl (clase), elementos primarios y secundarios"
  - "elemento primario de CTreeCtrl"
  - "controles de árbol, elementos primarios y secundarios"
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elementos primario y secundario del control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cualquier elemento de un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) puede tener una lista de subelementos, que se llaman elementos secundarios, asociada al.  Un elemento que tiene uno o más elementos secundarios se denomina elemento primario.  Un elemento secundario se muestra debajo de su elemento primario y se aplica sangría para indicar que es subordinado al elemento primario.  Un elemento que no tiene ningún elemento primario está en la parte superior de la jerarquía y se denomina elemento raíz.  
  
 En un momento dado, el estado de la lista de un elemento primario de elementos secundarios puede ser expandida o contraer.  Cuando expanda el estado, los elementos secundarios se muestran debajo del elemento primario.  Cuando se contrae, los elementos secundarios no se muestran.  En la lista alterna automáticamente entre estados expandidos y contraídas cuando el usuario hace doble clic en el elemento primario o, si el elemento primario tiene el estilo de **TVS\_HASBUTTONS** , cuando el usuario hace clic en el botón asociado al elemento primario.  Una aplicación puede expandir o contraer elementos secundarios mediante el miembro de [expandir](../Topic/CTreeCtrl::Expand.md) funcione.  
  
 Agrega un elemento a un control de árbol llamando a la función miembro de [InsertItem](../Topic/CTreeCtrl::InsertItem.md) .  Esta función devuelve un identificador del tipo de **HTREEITEM** , que identifica el elemento.  Al agregar un elemento, debe especificar el identificador del elemento primario del nuevo elemento.  Si especifica **nulo** o el valor de **TVI\_ROOT** en lugar de un identificador de elemento primario en la estructura de [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) o el parámetro de `hParent` , se agrega como elemento raíz.  
  
 Un control de árbol envía un mensaje de notificación de [TVN\_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) cuando la lista de un elemento primario de elementos secundarios está a punto de ser expandida o contraer.  La notificación ofrece la oportunidad de evitar el cambio o establecer los atributos del elemento primario que depende del estado de la lista de elementos secundarios.  Después de cambiar el estado de la lista, el control de árbol envía un mensaje de notificación de [TVN\_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) .  
  
 Cuando se expande una lista de elementos secundarios, se aplica sangría con relación al elemento primario.  Puede establecer la cantidad de sangría utilizando la función miembro de [SetIndent](../Topic/CTreeCtrl::SetIndent.md) o recuperar cantidad actual utilizando la función miembro de [GetIndent](../Topic/CTreeCtrl::GetIndent.md) .  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)