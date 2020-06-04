---
title: Procesar los mensajes de notificación del control de pestaña
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: cc322a038717d48f440df1ec571674cec80743ce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908062"
---
# <a name="processing-tab-control-notification-messages"></a>Procesar los mensajes de notificación del control de pestaña

A medida que los usuarios hacen clic en pestañas o botones, el control de pestaña ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en una pestaña, puede que desee preestablecer los datos de control en la página antes de mostrarla.

Procese los mensajes WM_NOTIFY del control de pestaña en la vista o la clase de cuadro de diálogo. Use el [Asistente para clases](reference/mfc-class-wizard.md) para crear una función controladora [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) con una instrucción switch basada en el mensaje de notificación que se está controlando. Para obtener una lista de las notificaciones que un control de pestaña puede enviar a su ventana primaria, consulte la sección **notificaciones** de [referencia de control de pestañas](/windows/win32/controls/tab-control-reference) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
