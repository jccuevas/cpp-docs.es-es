---
title: Procesar mensajes de notificación en el selector de fecha y hora controles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
dev_langs:
- C++
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1a3d4e224b1bcbc9a808387860a07c8ec85a0a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213605"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Procesar mensajes de notificación en los controles de selector de fecha y hora
Cuando los usuarios interactúan con la fecha y un control selector de hora, el control (`CDateTimeCtrl`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario abre el selector de fecha y hora para mostrar el control de calendario mensual incrustado, se envía la notificación DTN_DROPDOWN.  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente describe las distintas notificaciones enviadas por el control de selector de fecha y hora.  
  
-   DTN_DROPDOWN Notifica el elemento primario que el control de calendario mensual incrustado está a punto de mostrarse. Esta notificación se envía únicamente cuando no se ha establecido el estilo DTS_UPDOWN. Para obtener más información sobre esta notificación, consulte [acceso a Control de calendario mensual incrustado](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   DTN_CLOSEUP notifica el elemento primario que el control de calendario mensual incrustado está a punto de cerrarse. Esta notificación se envía únicamente cuando no se ha establecido el estilo DTS_UPDOWN.  
  
-   DTN_DATETIMECHANGE Notifica a la principal que se ha producido un cambio en el control.  
  
-   DTN_FORMAT Notifica es necesario el elemento primario que es el texto que se mostrará en un campo de devolución de llamada. Para obtener más información sobre esta notificación y campos de devolución de llamada, vea [usar campos de devolución de llamada en un Control Selector de hora de fecha y](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   DTN_FORMATQUERY solicita el elemento primario para proporcionar el tamaño máximo permitido de la cadena que se mostrará en un campo de devolución de llamada. Controlar esta notificación permite que el control para mostrar correctamente los resultados en todo momento, reducir el parpadeo en la presentación del control. Para obtener más información sobre esta notificación, consulte [usar campos de devolución de llamada en un Control Selector de hora de fecha y](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   Notifica a DTN_USERSTRING el elemento primario que el usuario ha terminado de editar el contenido del control de selector de fecha y hora. Esta notificación se envía únicamente cuando se ha establecido el estilo DTS_APPCANPARSE.  
  
-   DTN_WMKEYDOWN notifica al elemento primario cuando el usuario escribe en un campo de devolución de llamada. Controlar esta notificación para emular la misma respuesta teclado compatible con los campos de no devolución de llamada en un control de selector de fecha y hora. Para obtener más información sobre esta notificación, consulte [que admiten campos de devolución de llamada en un Control de DTP](/windows/desktop/Controls/date-and-time-picker-controls) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

