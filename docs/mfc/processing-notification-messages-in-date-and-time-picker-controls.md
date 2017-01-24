---
title: "Procesar mensajes de notificaci&#243;n en los controles de selector de fecha y hora | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTN_CLOSEUP"
  - "DTN_DATETIMECHANGE"
  - "DTN_DROPDOWN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl (clase), controlar notificaciones"
  - "DateTimePicker (control) [MFC]"
  - "DateTimePicker (control) [MFC], controlar notificaciones"
  - "DTN_CLOSEUP (notificación)"
  - "DTN_DATETIMECHANGE (notificación)"
  - "DTN_DROPDOWN (notificación)"
  - "DTN_FORMAT (notificación)"
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesar mensajes de notificaci&#243;n en los controles de selector de fecha y hora
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando los usuarios interactúan con el control selector de fecha y hora, el control \(`CDateTimeCtrl`\) envía mensajes de notificación a la ventana primaria, normalmente un objeto de vista o del diálogo.  Controle estos mensajes si desea hacer algo en respuesta.  Por ejemplo, cuando el usuario abra el selector de fecha y hora para mostrar el control incrustado de calendario mensual, se envía la notificación de **DTN\_DROPDOWN** .  
  
 Utilice la ventana Propiedades para agregar controladores de notificación a la clase primaria para los mensajes que desea implementar.  
  
 La lista siguiente describe las distintas notificaciones enviadas por el control selector de fecha y hora.  
  
-   **DTN\_DROPDOWN** Notifies el elemento primario que el control incrustado de calendario mensual se va a mostrar.  Esta notificación se envía cuando el estilo de **DTS\_UPDOWN** no se ha establecido.  Para obtener más información sobre esta notificación, vea [Acceso de Control incrustada de calendario mensual](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   **DTN\_CLOSEUP** Notifies el elemento primario que el control incrustado de calendario mensual está a punto de cerrarse.  Esta notificación se envía cuando el estilo de **DTS\_UPDOWN** no se ha establecido.  
  
-   **DTN\_DATETIMECHANGE** Notifies el elemento primario que un cambio ha producido en el control.  
  
-   **DTN\_FORMAT** Notifies el elemento primario que el texto es necesario mostrar en un campo de devolución de llamada.  Para obtener más información sobre estos campos de notificación y de devolución de llamada, vea [Utilizando los campos Callback en un Control del selector de fecha y hora](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **DTN\_FORMATQUERY** solicita el elemento primario para proporcionar el tamaño máximo permitido de la cadena que se mostrará en un campo de devolución de llamada.  Administrar esta notificación permite el control a correctamente muestra el resultado siempre, reduciendo el parpadeo dentro de presentación del control.  Para obtener más información sobre esta notificación, vea [Utilizando los campos Callback en un Control del selector de fecha y hora](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **DTN\_USERSTRING** Notifies el elemento primario que el usuario ha terminado de editar el contenido del control selector de fecha y hora.  Esta notificación se envía cuando se ha establecido el estilo de **DTS\_APPCANPARSE** .  
  
-   **DTN\_WMKEYDOWN** Notifies el elemento primario cuando el usuario escribe un campo de devolución de llamada.  Controla esta notificación para emular la misma respuesta de teclado compatible para campos de no de devolución de llamada en un control de selector de fecha y hora.  Para obtener más información sobre esta notificación, vea [Admitir los campos Callback en un Control de DTP](http://msdn.microsoft.com/library/windows/desktop/bb761726) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)