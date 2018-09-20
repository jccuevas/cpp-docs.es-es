---
title: Control elementos primarios y secundarios de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94bae5d06dd5b0e072d17588af045ec87a33fcc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374715"
---
# <a name="tree-control-parent-and-child-items"></a>Elementos primario y secundario del control de árbol

Cualquier elemento en un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener una lista de subelementos, que se denominan elementos secundarios, asociados con él. Un elemento que tiene uno o varios elementos secundarios se llama a un elemento primario. Un elemento secundario se muestra debajo de su elemento primario y se aplica sangría para indicar que es subordinado al elemento primario. Un elemento que no tiene ningún elemento primario es la parte superior de la jerarquía y se llama a un elemento raíz.

En un momento dado, el estado de la lista de un elemento primario de los elementos secundarios puede ser expandir o contraer. Cuando se expande el estado, se muestran los elementos secundarios por debajo del elemento primario. Cuando está contraído, no se muestran los elementos secundarios. La lista alterna automáticamente entre los Estados expandidos y contraídos cuando el usuario hace doble clic en el elemento primario o, si el elemento primario tiene el **TVS_HASBUTTONS** estilo, cuando el usuario hace clic en el botón asociado al elemento primario. Puede expandir o contraer los elementos secundarios mediante el uso de una aplicación la [expandir](../mfc/reference/ctreectrl-class.md#expand) función miembro.

Agregar un elemento a un control de árbol mediante una llamada a la [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) función miembro. Esta función devuelve un identificador de la **HTREEITEM** tipo, que identifica de forma única el elemento. Al agregar un elemento, debe especificar el identificador del elemento primario del elemento nuevo. Si especifica **NULL** o **TVI_ROOT** valor en lugar de un identificador de elemento primario en el [estructura TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa) estructura o *hParent* parámetro, el elemento se agrega como un elemento raíz.

Un control de árbol envía un [TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding) mensaje de notificación cuando la lista de elementos secundarios del elemento de un primario está a punto de expandirse o contraerse. La notificación le ofrece la oportunidad para evitar que el cambio o establecer los atributos del elemento primario que dependen del estado de la lista de elementos secundarios. Después de cambiar el estado de la lista, el control de árbol envía un [TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded) mensaje de notificación.

Cuando se expande una lista de elementos secundarios, se les aplica sangría en relación con el elemento primario. Puede establecer la cantidad de sangría mediante el [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) función miembro o recuperar la cantidad actual mediante el uso de la [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) función miembro.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

