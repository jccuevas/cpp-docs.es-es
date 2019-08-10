---
title: Notificaciones de un control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: bc4c027ff26df89539b22c6d04f1d1dc95fc459a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916399"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notificaciones de un control Rich Edit

Los mensajes de notificación informan de los eventos que afectan a un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Pueden ser procesados por la ventana primaria o, mediante la reflexión de mensajes, por el propio control Rich Edit. Los controles Rich Edit admiten todos los mensajes de notificación que se usan con controles de edición y otros adicionales. Puede determinar los mensajes de notificación en los que un control Rich Edit envía su ventana primaria estableciendo su "máscara de eventos".

Para establecer la máscara de eventos para un control Rich Edit, utilice la función miembro [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Puede recuperar la máscara de eventos actual para un control Rich Edit mediante la función miembro [GetEventMask (](../mfc/reference/cricheditctrl-class.md#geteventmask) .

En los párrafos siguientes se enumeran varias notificaciones específicas y sus usos:

- EN_MSGFILTER Handling The EN_MSGFILTER Notification permite una clase, ya sea el control Rich Edit o su ventana primaria, filtrar todas las entradas de teclado y del mouse en el control. El controlador puede impedir que se procese el mensaje del teclado o del mouse, o bien cambiar el mensaje modificando la estructura [MSGFILTER](/windows/desktop/api/richedit/ns-richedit-msgfilter) especificada.

- EN_PROTECTED controla el mensaje de notificación EN_PROTECTED para detectar cuando el usuario intenta modificar texto protegido. Para marcar un intervalo de texto como protegido, puede establecer el efecto de carácter protegido. Para obtener más información, vea [formato de caracteres en controles Rich Edit](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES puede permitir que el usuario coloque archivos en un control Rich Edit procesando el mensaje de notificación EN_DROPFILES. La estructura [ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-endropfiles) especificada contiene información sobre los archivos que se van a quitar.

- EN_SELCHANGE una aplicación puede detectar cuándo cambia la selección actual procesando el mensaje de notificación EN_SELCHANGE. El mensaje de notificación especifica una estructura [SELCHANGE](/windows/desktop/api/richedit/ns-richedit-selchange) que contiene información sobre la nueva selección.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
