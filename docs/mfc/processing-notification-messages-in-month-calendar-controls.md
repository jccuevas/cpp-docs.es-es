---
title: "Procesar mensajes de notificaci&#243;n en los controles de calendario mensual | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl (clase), estados de día"
  - "CMonthCalCtrl (clase), notificaciones"
  - "controles del calendario mensual, mensajes de notificación"
  - "notificaciones, para CMonthCalCtrl"
  - "notificaciones, control de calendario mensual"
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesar mensajes de notificaci&#243;n en los controles de calendario mensual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando los usuarios interactúan con el control de calendario mensual \(que selecciona fechas o ver un mes diferente\), el control \(`CMonthCalCtrl`\) envía mensajes de notificación a la ventana primaria, normalmente un objeto de vista o del diálogo.  Controle estos mensajes si desea hacer algo en respuesta.  Por ejemplo, cuando el usuario selecciona un nuevo mes para ver, podría proporcionar un conjunto de fechas que deben ser acentuadas.  
  
 Utilice la ventana Propiedades para agregar controladores de notificación a la clase primaria para los mensajes que desea implementar.  
  
 La lista siguiente describe las distintas notificaciones enviadas por el control de calendario mensual.  
  
-   **MCN\_GETDAYSTATE** solicita información acerca de los días se muestran en negrita.  Para obtener información sobre cómo administrar esta notificación, vea [Establecer el estado de Siguiente de un Control de calendario mensual](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   **MCN\_SELCHANGE** Notifies el elemento primario que la fecha o intervalo seleccionado de fecha ha cambiado.  
  
-   **MCN\_SELECT** Notifies el elemento primario que se ha creado una conversión explícita de fecha.  
  
## Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)