---
title: "Informaci&#243;n de elementos de control de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), información del elemento"
  - "controles de árbol, información del elemento"
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Informaci&#243;n de elementos de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) tienen varias miembro funcionan esa información de recuperación sobre elementos del control.  La función miembro de [GetItem](../Topic/CTreeCtrl::GetItem.md) recupera algunos o todos los datos asociados a un elemento.  Estos datos podría incluir el texto del elemento, estado, imágenes, el número de elementos secundarios, y un valor de datos de 32 bits definidos por la aplicación.  También existe una función de [SetItem](../Topic/CTreeCtrl::SetItem.md) que puede establecer algunos o todos los datos asociados a un elemento.  
  
 [GetItemState](../Topic/CTreeCtrl::GetItemState.md), [GetItemText](../Topic/CTreeCtrl::GetItemText.md), [GetItemData](../Topic/CTreeCtrl::GetItemData.md), y las funciones miembro de [GetItemImage](../Topic/CTreeCtrl::GetItemImage.md) recuperar los atributos individuales de un elemento.  Cada una de estas funciones tiene una función determinada correspondiente para establecer los atributos de un elemento.  
  
 La función miembro de [GetNextItem](../Topic/CTreeCtrl::GetNextItem.md) recupera el elemento del control de árbol que contiene la relación especificada al elemento actual.  Esta función puede recuperar el elemento primario de un elemento, el elemento visible siguiente o anterior, el primer elemento secundario, y así sucesivamente.  También hay funciones miembro para recorrer el árbol: [GetRootItem](../Topic/CTreeCtrl::GetRootItem.md), [GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md), [GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md), [GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md), [GetChildItem](../Topic/CTreeCtrl::GetChildItem.md), [GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md), [GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md), [GetParentItem](../Topic/CTreeCtrl::GetParentItem.md), [GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md), y [GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md).  
  
 La función miembro de [GetItemRect](../Topic/CTreeCtrl::GetItemRect.md) recupera el rectángulo delimitador para un elemento del control de árbol.  Las funciones miembro de [GetCount](../Topic/CTreeCtrl::GetCount.md) y de [GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md) recuperan un recuento de los elementos en un control de árbol y un recuento de los elementos que están actualmente visible en la ventana del control de árbol, respectivamente.  Puede asegurarse de que un elemento determinado está visible llamando a la función miembro de [EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md) .  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)