---
title: Procesar mensajes de notificación en los controles de selector de fecha y hora
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: 3c568d231cc02b2529a4d97ab7faed51c1737b19
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621002"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Procesar mensajes de notificación en los controles de selector de fecha y hora

A medida que los usuarios interactúan con el control selector de fecha y hora, el control ( `CDateTimeCtrl` ) envía mensajes de notificación a su ventana primaria, normalmente una vista o un objeto de cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario abre el selector de fecha y hora para mostrar el control de calendario mensual incrustado, se envía la notificación de DTN_DROPDOWN.

Use el [Asistente para clases](reference/mfc-class-wizard.md) para agregar controladores de notificación a la clase primaria para los mensajes que desee implementar.

En la lista siguiente se describen las distintas notificaciones enviadas por el control de selector de fecha y hora.

- DTN_DROPDOWN notifica al elemento primario que el control de calendario mensual incrustado está a punto de mostrarse. Esta notificación solo se envía cuando no se ha establecido el estilo de DTS_UPDOWN. Para obtener más información sobre esta notificación, vea [obtener acceso al control de calendario mensual incrustado](accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP notifica al elemento primario que el control de calendario mensual incrustado está a punto de cerrarse. Esta notificación solo se envía cuando no se ha establecido el estilo de DTS_UPDOWN.

- DTN_DATETIMECHANGE notifica al elemento primario que se ha producido un cambio en el control.

- DTN_FORMAT notifica al elemento primario que el texto debe mostrarse en un campo de devolución de llamada. Para obtener más información sobre estos campos de notificación y devolución de llamada, vea [usar campos de devolución de llamada en un control de selector de fecha y hora](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY solicita que el elemento primario proporcione el tamaño máximo permitido de la cadena que se mostrará en un campo de devolución de llamada. Controlar esta notificación permite que el control muestre correctamente el resultado en todo momento, lo que reduce el parpadeo en la pantalla del control. Para obtener más información sobre esta notificación, vea [usar campos de devolución de llamada en un control de selector de fecha y hora](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING notifica al elemento primario que el usuario ha terminado de editar el contenido del control selector de fecha y hora. Esta notificación solo se envía cuando se ha establecido el estilo de DTS_APPCANPARSE.

- DTN_WMKEYDOWN notifica al elemento primario cuando el usuario escribe en un campo de devolución de llamada. Controle esta notificación para emular la misma respuesta de teclado compatible con los campos que no son de devolución de llamada en un control de selector de fecha y hora. Para obtener más información sobre esta notificación, vea [admitir campos de devolución de llamada en un control de DTP](/windows/win32/Controls/date-and-time-picker-controls) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Usar CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Permite](controls-mfc.md)
