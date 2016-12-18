---
title: "Procesar mensajes de notificaci&#243;n en los controles de lista | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CListCtrl (clase), procesar notificaciones"
  - "procesar notificaciones"
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesar mensajes de notificaci&#243;n en los controles de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como los usuarios hacen clic en encabezados de columna, arrastre los iconos, etiquetas de edición, etc., el control de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\) envía mensajes de notificación a su ventana primaria.  Controle estos mensajes si desea hacer algo en respuesta.  Por ejemplo, cuando el usuario hace clic en un encabezado de columna, quizás desee ordenar los elementos según el contenido de la columna hace clic, como en Microsoft Outlook.  
  
 Mensajes de **WM\_NOTIFY** de control de la clase de vista o del diálogo.  Utilice la ventana Propiedades para crear una función de controlador de [OnChildNotify](../Topic/CWnd::OnChildNotify.md) con una instrucción switch basada en se manejando qué mensaje de notificación.  
  
 Para obtener una lista de las notificaciones que un control de lista puede enviar a su ventana primaria, vea [Referencia del Control de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774737) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)