---
title: Controlar los mensajes reflejados
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 8907b432cf4dabad33c0925b841f65dfc57c6295
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620143"
---
# <a name="handling-reflected-messages"></a>Controlar los mensajes reflejados

La reflexión de mensajes le permite controlar los mensajes de un control, como **WM_CTLCOLOR**, **WM_COMMAND**y **WM_NOTIFY**, dentro del propio control. Esto hace que el control sea más independiente y portátil. El mecanismo funciona con controles comunes de Windows, así como con controles ActiveX (anteriormente denominados controles OLE).

La reflexión de mensajes le permite volver a usar las `CWnd` clases derivadas de más fácilmente. La reflexión de mensajes funciona a través de [CWnd:: OnChildNotify](reference/cwnd-class.md#onchildnotify), mediante entradas especiales de mapa de mensajes de **ON_XXX_REFLECT** : por ejemplo, **ON_CTLCOLOR_REFLECT** y **ON_CONTROL_REFLECT**. La [Nota técnica 62](tn062-message-reflection-for-windows-controls.md) explica la reflexión de mensajes con más detalle.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Más información sobre la reflexión de mensajes](tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control común](tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control ActiveX](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](declaring-message-handler-functions.md)
