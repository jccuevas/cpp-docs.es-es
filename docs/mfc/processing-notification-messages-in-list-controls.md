---
title: Procesar mensajes de notificación en los controles de lista
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 92111e3e0a4869ca06b89d2d18d38aab9f10ab7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908095"
---
# <a name="processing-notification-messages-in-list-controls"></a>Procesar mensajes de notificación en los controles de lista

A medida que los usuarios hacen clic en los encabezados de columna, arrastran iconos, editan etiquetas, etc., el control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en un encabezado de columna, es posible que desee ordenar los elementos según el contenido de la columna en la que se hizo clic, como en Microsoft Outlook.

Procese los mensajes WM_NOTIFY del control de lista en la vista o la clase de cuadro de diálogo. Use el [Asistente para clases](reference/mfc-class-wizard.md) para crear una función controladora [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) con una instrucción switch basada en el mensaje de notificación que se está controlando.

Para obtener una lista de las notificaciones que un control de lista puede enviar a su ventana primaria, vea [referencia de control de vista de lista](/windows/win32/Controls/list-view-control-reference) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
