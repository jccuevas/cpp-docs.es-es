---
title: "Acceso al control de calendario mensual incrustado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl (clase), obtener acceso a controles incrustados"
  - "CMonthCalCtrl (clase), cambiar la fuente"
  - "DateTimePicker (control) [MFC]"
  - "DateTimePicker (control) [MFC], obtener acceso al calendario mensual"
  - "controles del calendario mensual, cambiar la fuente"
  - "controles del calendario mensual, incrustados en el selector de fecha y hora"
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Acceso al control de calendario mensual incrustado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El objeto incrustado de control de calendario mensual se puede tener acceso desde el objeto de `CDateTimeCtrl` con una llamada a la función miembro de [GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md) .  
  
> [!NOTE]
>  Se utiliza el control incrustado de calendario mensual sólo cuando el control selector de fecha y hora no tiene el estilo de **DTS\_UPDOWN** establecido.  
  
 Esto es útil si desea modificar ciertos atributos antes de que se muestre el control incrustado.  Para ello, controle la notificación de **DTN\_DROPDOWN** , recupera el control de calendario mensual \(mediante [CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)\), y se crean las modificaciones.  Desgraciadamente, el control de calendario mensual no es persistente.  
  
 Es decir cuando se crean las solicitudes de usuario la presentación del control de calendario mensual, un nuevo control de calendario mensual \(antes de la notificación de **DTN\_DROPDOWN** \).  Se destruye el control \(después de la notificación de **DTN\_CLOSEUP** \) cuando lo despedido por el usuario.  Esto significa que los atributos que se modifique, antes de que se muestre el control incrustado, se pierde cuando se descarta el control incrustado.  
  
 El ejemplo siguiente se muestra este procedimiento, mediante un controlador para la notificación de **DTN\_DROPDOWN** .  El código cambia el color de fondo del control de calendario mensual, con una llamada a [SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md), para gris.  El código es la siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 Como se indicó anteriormente, todas las modificaciones a las propiedades del control de calendario mensual se pierden, con dos excepciones, cuando se descarta el control incrustado.  La primera excepción, los colores del control de calendario mensual, se ha explicado ya.  La segunda excepción es la fuente utilizada por el control de calendario mensual.  Puede modificar la fuente predeterminada mediante una llamada a [CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md), pasando el identificador de una fuente existente.  El ejemplo siguiente \(donde es el objeto `m_dtPicker` de control de fecha y hora\) muestra un método posible:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 Una vez que han cambiado se almacena y se utiliza la fuente, con una llamada a `CDateTimeCtrl::SetMonthCalFont`, la nueva fuente la próxima vez que un calendario mensual debe mostrarse.  
  
## Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)