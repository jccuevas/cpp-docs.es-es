---
title: Controlar los mensajes reflejados
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 9b580c0c8b8fc970d69f5c57f69bbbbe65e22497
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449873"
---
# <a name="handling-reflected-messages"></a>Controlar los mensajes reflejados

Mensaje de reflexión le permite controlar los mensajes para un control, como **WM_CTLCOLOR**, **WM_COMMAND**, y **WM_NOTIFY**, dentro del propio control. Esto hace que el control más autocontenida y portátil. El mecanismo funciona con los controles comunes de Windows, así como con los controles ActiveX (anteriormente denominados controles OLE).

Reflexión de mensajes permite reutilizar la `CWnd`-las clases derivadas con más facilidad. Funciona a través de la reflexión de mensajes [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), uso especial **ON_XXX_REFLECT** entradas de mapa de mensajes: por ejemplo, **ON_CTLCOLOR_REFLECT** y **ON_CONTROL_REFLECT**. [Nota técnica 62](../mfc/tn062-message-reflection-for-windows-controls.md) explica la reflexión de mensajes con más detalle.

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Más información sobre la reflexión de mensajes](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control común](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
