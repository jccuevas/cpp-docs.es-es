---
title: "Informaci&#243;n sobre herramientas en ventanas no derivadas de CFrameWnd | Microsoft Docs"
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
  - "controles [MFC], información sobre herramientas"
  - "habilitar la información sobre herramientas"
  - "funciones controladoras, información sobre herramientas"
  - "Ayuda, información sobre herramientas para controles"
  - "TOOLTIPTEXT (estructura)"
  - "TTN_NEEDTEXT (mensaje)"
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n sobre herramientas en ventanas no derivadas de CFrameWnd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta familia de caso cubre habilitar la información sobre herramientas de los controles contenidos en una ventana que no se deriva de [CFrameWnd](../mfc/reference/cframewnd-class.md).  El artículo [Información sobre herramientas de barras de herramientas](../mfc/toolbar-tool-tips.md) proporciona información sobre la información sobre herramientas de los controles en `CFrameWnd`.  
  
 Temas cubiertos en incluyen de la familia de artículo:  
  
-   [Habilitar información sobre herramientas](../mfc/enabling-tool-tips.md)  
  
-   [Administrar la notificación de TTN\_NEEDTEXT para informaciones sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [La estructura de TOOLTIPTEXT](../mfc/tooltiptext-structure.md)  
  
 La información sobre herramientas aparecen automáticamente para los botones y otros controles contenidos en una ventana primaria derivada de `CFrameWnd`.  Esto es porque `CFrameWnd` tiene un controlador predeterminado para la notificación de [TTN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) , que controla las notificaciones de **TTN\_NEEDTEXT** de los controles de información sobre herramientas asociados a los controles.  
  
 Sin embargo, no se llama a este controlador predeterminado cuando la notificación de **TTN\_NEEDTEXT** se envía de un control de información sobre herramientas asociado a un control en una ventana que no es `CFrameWnd`, como un control en un cuadro de diálogo o una vista de formulario.  Por consiguiente, es necesario que proporcione una función controladora para el mensaje de notificación de **TTN\_NEEDTEXT** para mostrar información sobre herramientas para los controles secundarios.  
  
 La información sobre herramientas predeterminadas proporcionadas para las ventanas por [CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md) no tienen texto asociado a ellas.  Para recuperar el texto de la información sobre herramientas muestra, notificación de **TTN\_NEEDTEXT** se envía a la ventana primaria de control tooltip justo antes de que se muestra la ventana de la información sobre herramientas.  Si no hay ningún controlador para que este mensaje asignar un valor al miembro de **pszText** de la estructura de **TOOLTIPTEXT** , no habrá texto mostrado para la información sobre herramientas.  
  
## Vea también  
 [Información sobre herramientas](../mfc/tool-tips.md)