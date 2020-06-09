---
title: Notificaciones de un control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 206fc02088f6531338bf2aa4cf272a1da096bae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622228"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notificaciones de un control Rich Edit

Los mensajes de notificación informan de los eventos que afectan a un control Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)). Pueden ser procesados por la ventana primaria o, mediante la reflexión de mensajes, por el propio control Rich Edit. Los controles Rich Edit admiten todos los mensajes de notificación que se usan con controles de edición y otros adicionales. Puede determinar los mensajes de notificación en los que un control Rich Edit envía su ventana primaria estableciendo su "máscara de eventos".

Para establecer la máscara de eventos para un control Rich Edit, utilice la función miembro [SetEventMask](reference/cricheditctrl-class.md#seteventmask) . Puede recuperar la máscara de eventos actual para un control Rich Edit mediante la función miembro [GetEventMask (](reference/cricheditctrl-class.md#geteventmask) .

En los párrafos siguientes se enumeran varias notificaciones específicas y sus usos:

- EN_MSGFILTER controlar la notificación de EN_MSGFILTER permite una clase, ya sea el control Rich Edit o su ventana primaria, filtrar todas las entradas de teclado y del mouse en el control. El controlador puede impedir que se procese el mensaje del teclado o del mouse, o bien cambiar el mensaje modificando la estructura [MSGFILTER](/windows/win32/api/richedit/ns-richedit-msgfilter) especificada.

- EN_PROTECTED controlar el mensaje de notificación de EN_PROTECTED para detectar cuándo el usuario intenta modificar texto protegido. Para marcar un intervalo de texto como protegido, puede establecer el efecto de carácter protegido. Para obtener más información, vea [formato de caracteres en controles Rich Edit](character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES puede permitir que el usuario coloque archivos en un control Rich Edit procesando el mensaje de notificación de EN_DROPFILES. La estructura [ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles) especificada contiene información sobre los archivos que se van a quitar.

- EN_SELCHANGE una aplicación puede detectar cuándo cambia la selección actual procesando el mensaje de notificación de EN_SELCHANGE. El mensaje de notificación especifica una estructura [SELCHANGE](/windows/win32/api/richedit/ns-richedit-selchange) que contiene información sobre la nueva selección.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
