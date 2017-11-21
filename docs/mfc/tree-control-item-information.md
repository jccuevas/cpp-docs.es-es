---
title: "Información de elementos de Control de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a0747147f247f7400e2455fdf5f63e61378e96e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-information"></a>Información de elementos de control de árbol
Controles de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) tiene un número de funciones de miembro que recuperan información sobre los elementos del control. El [GetItem](../mfc/reference/ctreectrl-class.md#getitem) función miembro recupera algunos o todos los datos asociados a un elemento. Estos datos podrían incluir el texto del elemento, estado, imágenes, recuento de elementos secundarios y un valor de datos definido por la aplicación de 32 bits. También hay un [SetItem](../mfc/reference/ctreectrl-class.md#setitem) función que puede establecer algunos o todos los datos asociados a un elemento.  
  
 El [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext), [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata), y [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) funciones miembro recuperan atributos individuales de un elemento. Cada una de estas funciones tiene una función Set correspondiente para establecer los atributos de un elemento.  
  
 El [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) función miembro recupera el elemento de control de árbol que mantiene la relación especificada al elemento actual. Esta función puede recuperar primario de un elemento, el elemento visible anterior o siguiente, el primer elemento secundario y así sucesivamente. También existen funciones de miembro para recorrer el árbol: [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), y [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).  
  
 El [función miembro GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) función miembro recupera el rectángulo delimitador para un elemento de control de árbol. El [GetCount](../mfc/reference/ctreectrl-class.md#getcount) y [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) funciones miembro recuperan un recuento de los elementos de un control de árbol y un recuento de los elementos que están visibles en la ventana del control de árbol, respectivamente. Puede asegurarse de que un determinado elemento está visible mediante una llamada a la [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

