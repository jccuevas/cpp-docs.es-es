---
title: Control elementos primarios y secundarios de árbol | Documentos de Microsoft
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
ms.openlocfilehash: 260cbf640f6c57e4b145d01e8f883025a4dc6507
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-parent-and-child-items"></a>Elementos primario y secundario del control de árbol
Cualquier elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener una lista de subelementos, que se denominan elementos secundarios, asociados a él. Un elemento que tiene uno o más elementos secundarios se denomina un elemento primario. Un elemento secundario se muestra debajo de su elemento primario y se aplica una sangría para indicar que es subordinado al elemento primario. Un elemento que no tiene elemento primario está en la parte superior de la jerarquía y se llama a un elemento raíz.  
  
 En un momento dado, el estado de la lista de elementos secundarios del elemento de un primario puede ser expandir o contraer. Cuando se expande el estado, los elementos secundarios se muestran debajo del elemento primario. Cuando esta se contrae, no se muestran los elementos secundarios. La lista alterna automáticamente entre los Estados expandidos y contraídos cuando el usuario hace doble clic en el elemento primario o, si el elemento primario tiene el **TVS_HASBUTTONS** estilo, cuando el usuario hace clic en el botón asociado al elemento primario. Una aplicación puede expandir o contraer los elementos secundarios utilizando la [expandir](../mfc/reference/ctreectrl-class.md#expand) función miembro.  
  
 Agregar un elemento a un control de árbol mediante una llamada a la [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) función miembro. Esta función devuelve un identificador de la **HTREEITEM** tipo, que identifica de forma única el elemento. Al agregar un elemento, debe especificar el identificador del elemento primario del elemento nuevo. Si especifica **NULL** o **TVI_ROOT** valor en lugar de un identificador de elemento primario en el [estructura TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) estructura o `hParent` parámetro, se agrega el elemento raíz elemento.  
  
 Un control de árbol envía un [TVN_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) recibe un mensaje de notificación cuando la lista de un elemento primario de los elementos secundarios se va a expandir o contraer. La notificación ofrece la oportunidad para evitar que el cambio o establecer los atributos del elemento primario que dependen del estado de la lista de elementos secundarios. Después de cambiar el estado de la lista, el control de árbol envía un [TVN_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) mensaje de notificación.  
  
 Cuando se expande una lista de elementos secundarios, se aplica una sangría respecto al elemento primario. Puede establecer la cantidad de sangría mediante el [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) función miembro o recuperar la cantidad actual mediante el uso de la [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

