---
title: Procesar mensajes de notificación en el selector de fecha y hora controles | Documentos de Microsoft
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
ms.openlocfilehash: 53c45f664dec2a553210187514b28f1ba3c2ed9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349179"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Procesar mensajes de notificación en los controles de selector de fecha y hora
Cuando los usuarios interactúan con la fecha y el control de selector de tiempo, el control (`CDateTimeCtrl`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario abre el selector de fecha y hora para mostrar el control de calendario mensual incrustado, el **DTN_DROPDOWN** se envía la notificación.  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente describe las distintas notificaciones enviadas por el control de selector de fecha y hora.  
  
-   **DTN_DROPDOWN** notifica el registro primario que el control de calendario mensual incrustado está a punto de mostrarse. Esta notificación sólo se envía cuando el **DTS_UPDOWN** no se estableció el estilo. Para obtener más información sobre esta notificación, vea [obtiene acceso a Control de calendario mensual incrustado](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   **DTN_CLOSEUP** notifica el registro primario que el control de calendario mensual incrustado está a punto de cerrarse. Esta notificación sólo se envía cuando el **DTS_UPDOWN** no se estableció el estilo.  
  
-   **DTN_DATETIMECHANGE** notifica el registro primario que se ha producido un cambio en el control.  
  
-   **DTN_FORMAT** notifica que el elemento primario que se necesita el texto que se mostrará en un campo de devolución de llamada. Para obtener más información sobre esta notificación y campos de devolución de llamada, vea [usar campos de devolución de llamada en un Control Date and Time selector](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **DTN_FORMATQUERY** solicita el elemento primario para proporcionar el tamaño máximo permitido de la cadena que se mostrará en un campo de devolución de llamada. Controlar esta notificación permite al control mostrar correctamente los resultados en todo momento, reduciendo el parpadeo en la presentación del control. Para obtener más información sobre esta notificación, vea [usar campos de devolución de llamada en un Control Date and Time selector](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **DTN_USERSTRING** notifica que el elemento primario que el usuario ha terminado de editar el contenido del control de selector de fecha y hora. Esta notificación sólo se envía cuando el **DTS_APPCANPARSE** se ha establecido el estilo.  
  
-   **DTN_WMKEYDOWN** notifica el elemento primario cuando el usuario escribe en un campo de devolución de llamada. Controlar esta notificación para emular la misma respuesta de teclado compatible con campos de devolución de llamada no en un control de selector de fecha y hora. Para obtener más información sobre esta notificación, vea [admitir campos de devolución de llamada en un Control DTP](http://msdn.microsoft.com/library/windows/desktop/bb761726) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

