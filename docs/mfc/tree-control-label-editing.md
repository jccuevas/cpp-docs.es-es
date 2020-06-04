---
title: Edición de etiquetas de control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 4b53d2c8e5a26a4dc37dfd7ae0710748bcd27bf6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741232"
---
# <a name="tree-control-label-editing"></a>Edición de etiquetas de control de árbol

El usuario puede editar directamente las etiquetas de los elementos de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) que tenga el estilo **TVS_EDITLABELS** . El usuario comienza a editar haciendo clic en la etiqueta del elemento que tiene el foco. Una aplicación comienza a editarse mediante la función miembro [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) . El control de árbol envía la notificación cuando comienza la edición y cuando se cancela o se completa. Cuando se completa la edición, usted es responsable de actualizar la etiqueta del elemento, si es necesario.

Cuando comienza la edición de la etiqueta, un control de árbol envía un mensaje de notificación [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) . Al procesar esta notificación, puede permitir la edición de algunas etiquetas y evitar la edición de otras. Devolver 0 permite la edición y devolver un valor distinto de cero lo evita.

Cuando la edición de etiquetas se cancela o se completa, un control de árbol envía un mensaje de notificación [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) . El parámetro *lParam* es la dirección de una estructura [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . El miembro del **elemento** es una estructura [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) que identifica el elemento e incluye el texto editado. Usted es responsable de actualizar la etiqueta del elemento, si es necesario, después de validar la cadena modificada. El miembro *miembros pszText* de `TV_ITEM` es 0 si se cancela la edición.

Durante la edición de etiquetas, normalmente en respuesta al mensaje de notificación [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) , puede obtener un puntero al control de edición que se usa para la edición de etiquetas mediante la función miembro [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) . Puede llamar a la función miembro [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) del control de edición para limitar la cantidad de texto que un usuario puede escribir o subclase del control de edición para interceptar y descartar los caracteres no válidos. Tenga en cuenta, sin embargo, que el control de edición solo se muestra *después* de enviar **TVN_BEGINLABELEDIT** .

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
