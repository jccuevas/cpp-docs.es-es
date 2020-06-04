---
title: Procesar notificaciones del control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: bc811763fe3f4717b8baaeb4a23df1ae59bb1979
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908137"
---
# <a name="processing-header-control-notifications"></a>Procesar notificaciones del control de encabezado

En la vista o la clase de cuadro de diálogo, use el [Asistente para clases](reference/mfc-class-wizard.md) con el fin de crear una función controladora [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) con una instrucción switch para los mensajes de notificación de control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) que desee controlar (consulte [asignación de mensajes a Funciones](../mfc/reference/mapping-messages-to-functions.md)). Las notificaciones se envían a la ventana primaria cuando el usuario hace clic o hace doble clic en un elemento de encabezado, arrastra un divisor entre los elementos, etc.

Los mensajes de notificación asociados a un control de encabezado se enumeran en [referencia de control de encabezado](/windows/win32/controls/header-control-reference) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
