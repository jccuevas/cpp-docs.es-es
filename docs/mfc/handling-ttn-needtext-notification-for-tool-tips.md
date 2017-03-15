---
title: "Controlar la notificaci&#243;n TTN_NEEDTEXT para la informaci&#243;n sobre herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TTN_NEEDTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "notificaciones, información sobre herramientas"
  - "información sobre herramientas [C++], notificaciones"
  - "TTN_NEEDTEXT (mensaje)"
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Controlar la notificaci&#243;n TTN_NEEDTEXT para la informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como parte de [habilitar información sobre herramientas](../mfc/enabling-tool-tips.md), administre el mensaje de **TTN\_NEEDTEXT** por que agrega la siguiente entrada al mensaje de la ventana propietaria asignado:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 La función miembro que se llamará cuando el texto es necesario para el botón.  
  
 Observe que el identificador de una información sobre herramientas siempre es 0.  
  
 Declare la función controladora en la definición de clase de la manera siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 donde los parámetros título en cursivas:  
  
 `id`  
 Identificador del control que envió la notificación.  No usado.  El id. del control se toma de la estructura de **NMHDR** .  
  
 `pNMHDR`  
 Un puntero a la estructura de [NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258) .  Esta estructura también se describe más detalladamente en [La estructura de TOOLTIPTEXT](../mfc/tooltiptext-structure.md).  
  
 `pResult`  
 Un puntero al código de resultado que puede establecer antes de volver.  Los controladores de**TTN\_NEEDTEXT** pueden omitir el parámetro de `pResult` .  
  
 Como ejemplo de un controlador de notificación de formulario\- vista:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Llamada `EnableToolTips` \(este fragmento tomado de `OnInitDialog`\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)