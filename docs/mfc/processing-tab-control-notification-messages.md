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
ms.openlocfilehash: 32e1b5954bc3f09f16c5516fc1c143dac716bc41
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693237"
---
# <a name="processing-tab-control-notification-messages"></a>Procesar los mensajes de notificación del control de pestaña

Como los usuarios, haga clic en fichas o botones, el control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en una pestaña, puede preestablecer datos de control en la página antes de mostrarlo.

Procese los mensajes WM_NOTIFY desde el control de ficha en la clase de vista o cuadro de diálogo. Utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch en función de qué mensaje de notificación que se está controlando. Para obtener una lista de las notificaciones de un control de ficha puede enviar a su ventana primaria, vea el **notificaciones** sección de [referencia de Control de ficha](/windows/desktop/controls/tab-control-reference) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

