---
title: Mensajes de notificación de controles de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 90e2e112d7862dfed7d8af31cfb72ff45633a2c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181649"
---
# <a name="tree-control-notification-messages"></a>Mensajes de notificación de controles de árbol

Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía los siguientes mensajes de notificación como mensajes WM_NOTIFY:

|Mensaje de notificación|Descripción|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Señala el inicio de una operación de arrastrar y colocar|
|TVN_BEGINLABELEDIT|Señala el inicio de la edición en contexto de etiquetas.|
|TVN_BEGINRDRAG|Señala el inicio de una operación de arrastrar y colocar, con el botón secundario del mouse|
|TVN_DELETEITEM|Indica la eliminación de un elemento específico|
|TVN_ENDLABELEDIT|Señala el final de la edición de etiqueta|
|TVN_GETDISPINFO|Información de las solicitudes que requiere el control de árbol para mostrar un elemento|
|TVN_ITEMEXPANDED|Indica que la lista de un elemento primario de los elementos secundarios se ha expandido o contraído|
|TVN_ITEMEXPANDING|Indica que la lista de elementos secundarios del elemento de un primario está a punto de expandirse o contraerse|
|TVN_KEYDOWN|Señala un evento de teclado|
|TVN_SELCHANGED|Indica que la selección ha cambiado de un elemento a otro|
|TVN_SELCHANGING|Indica que la selección está a punto de modificarse desde un elemento a otro|
|TVN_SETDISPINFO|Notificación para actualizar la información que se mantiene para un elemento|

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
