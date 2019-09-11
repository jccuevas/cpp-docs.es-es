---
title: Procesar mensajes de notificación en los controles de calendario mensual
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908076"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Procesar mensajes de notificación en los controles de calendario mensual

A medida que los usuarios interactúan con el control de calendario mensual (al seleccionar fechas y/o ver un`CMonthCalCtrl`mes diferente), el control () envía mensajes de notificación a su ventana primaria, normalmente una vista o un objeto de cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario selecciona un nuevo mes para verlo, puede proporcionar un conjunto de fechas que se deben resaltar.

Use el [Asistente para clases](reference/mfc-class-wizard.md) para agregar controladores de notificación a la clase primaria para los mensajes que desee implementar.

En la lista siguiente se describen las distintas notificaciones enviadas por el control de calendario mensual.

- MCN_GETDAYSTATE solicita información sobre los días que se deben mostrar en negrita. Para obtener información sobre cómo controlar esta notificación, vea [establecer el estado de día de un control de calendario mensual](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- MCN_SELCHANGE notifica al elemento primario que la fecha o el intervalo de fechas seleccionado han cambiado.

- MCN_SELECT notifica al elemento primario que se ha realizado una selección de fecha explícita.

## <a name="see-also"></a>Vea también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
