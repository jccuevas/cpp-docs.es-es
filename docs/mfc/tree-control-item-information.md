---
title: Información de Control de elemento de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a61d6dbf2084288d6015e8fc2c08bfc2283d4ba4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391025"
---
# <a name="tree-control-item-information"></a>Información de elementos de control de árbol

Controles de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) tiene un número de funciones miembro que recuperan información sobre los elementos del control. El [GetItem](../mfc/reference/ctreectrl-class.md#getitem) función miembro recupera algunos o todos los datos asociados a un elemento. Estos datos podrían incluir el texto del elemento, estado, imágenes, recuento de elementos secundarios y un valor de datos definido por la aplicación de 32 bits. También hay un [SetItem](../mfc/reference/ctreectrl-class.md#setitem) función que puede establecer algunos o todos los datos asociados a un elemento.

El [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext), [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata), y [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) funciones miembro recuperación atributos individuales de un elemento. Cada una de estas funciones tiene una función de conjunto correspondiente para establecer los atributos de un elemento.

El [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) función miembro recupera el elemento de control de árbol que mantiene la relación especificada al elemento actual. Esta función puede recuperar primario de un elemento, el elemento visible anterior o siguiente, el primer elemento secundario y así sucesivamente. También hay funciones de miembro para recorrer el árbol: [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), y [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).

El [función miembro GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) función miembro recupera el rectángulo delimitador de un elemento de control de árbol. El [GetCount](../mfc/reference/ctreectrl-class.md#getcount) y [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) funciones miembro recuperación un recuento de los elementos de un control de árbol y un recuento de los elementos que están actualmente visibles en la ventana del control de árbol, respectivamente. Puede asegurarse de que un elemento concreto está visible mediante una llamada a la [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) función miembro.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

