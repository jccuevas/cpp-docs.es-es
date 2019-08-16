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
ms.openlocfilehash: 97abde8285a3baf307df79fd97d4f9a379c8f58f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507835"
---
# <a name="processing-tab-control-notification-messages"></a>Procesar los mensajes de notificación del control de pestaña

A medida que los usuarios hacen clic en pestañas o botones, el control de pestaña ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en una pestaña, puede que desee preestablecer los datos de control en la página antes de mostrarla.

Procese los mensajes WM_NOTIFY del control de pestaña en la vista o la clase de cuadro de diálogo. Utilice la ventana Propiedades para crear una función controladora [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) con una instrucción switch basada en el mensaje de notificación que se está controlando. Para obtener una lista de las notificaciones que un control de pestaña puede enviar a su ventana primaria , consulte la sección notificaciones de [referencia de control](/windows/win32/controls/tab-control-reference) de pestañas en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
