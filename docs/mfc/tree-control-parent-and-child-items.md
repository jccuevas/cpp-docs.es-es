---
title: Elementos primario y secundario del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513964"
---
# <a name="tree-control-parent-and-child-items"></a>Elementos primario y secundario del control de árbol

Cualquier elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener una lista de subelementos, que se denominan elementos secundarios, asociados a él. Un elemento que tiene uno o más elementos secundarios se denomina elemento primario. Un elemento secundario se muestra debajo de su elemento primario y se le aplica una sangría para indicar que está subordinado al primario. Un elemento que no tiene ningún elemento primario se encuentra en la parte superior de la jerarquía y se denomina elemento raíz.

En un momento dado, el estado de la lista de elementos secundarios de un elemento primario puede expandirse o contraerse. Cuando se expande el estado, los elementos secundarios se muestran debajo del elemento primario. Cuando se contrae, no se muestran los elementos secundarios. La lista alterna automáticamente entre los Estados expandido y contraído cuando el usuario hace doble clic en el elemento primario o, si el elemento primario tiene el estilo **TVS_HASBUTTONS** , cuando el usuario hace clic en el botón asociado al elemento primario. Una aplicación puede expandir o contraer los elementos secundarios mediante la función miembro [Expand](../mfc/reference/ctreectrl-class.md#expand) .

Para agregar un elemento a un control de árbol, llame a la función miembro [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Esta función devuelve un identificador del tipo **HTREEITEM** , que identifica de forma única el elemento. Al agregar un elemento, debe especificar el identificador del elemento primario del nuevo elemento. Si especifica **null** o el valor **TVI_ROOT** en lugar de un identificador de elemento primario en la estructura [TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) o el parámetro *hParent* , el elemento se agrega como un elemento raíz.

Un control de árbol envía un mensaje de notificación [TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding) cuando la lista de elementos secundarios de un elemento primario está a punto de expandirse o contraerse. La notificación le ofrece la oportunidad de evitar el cambio o de establecer los atributos del elemento primario que dependen del estado de la lista de elementos secundarios. Después de cambiar el estado de la lista, el control de árbol envía un mensaje de notificación [TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded) .

Cuando se expande una lista de elementos secundarios, se aplica una sangría relativa al elemento primario. Puede establecer la cantidad de sangría mediante la función miembro [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) o recuperar la cantidad actual mediante la función miembro [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) .

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
