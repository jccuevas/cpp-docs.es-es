---
title: Procesar mensajes de notificación en los controles de lista
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: e93e91a3219f81bf4027549fc84f1c85c8defb5b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507866"
---
# <a name="processing-notification-messages-in-list-controls"></a>Procesar mensajes de notificación en los controles de lista

A medida que los usuarios hacen clic en los encabezados de columna, arrastran iconos, editan etiquetas, etc., el control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en un encabezado de columna, es posible que desee ordenar los elementos según el contenido de la columna en la que se hizo clic, como en Microsoft Outlook.

Procese los mensajes WM_NOTIFY del control de lista en la vista o la clase de cuadro de diálogo. Utilice la ventana Propiedades para crear una función controladora [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) con una instrucción switch basada en el mensaje de notificación que se está controlando.

Para obtener una lista de las notificaciones que un control de lista puede enviar a su ventana primaria, vea [referencia de control de vista de lista](/windows/win32/Controls/list-view-control-reference) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
