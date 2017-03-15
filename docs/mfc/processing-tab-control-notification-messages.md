---
title: "Procesar los mensajes de notificaci&#243;n del control de pesta&#241;a | Microsoft Docs"
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
  - "CTabCtrl (clase), procesar notificaciones"
  - "notificaciones, procesar en CTabCtrl"
  - "notificaciones, controles de fichas"
  - "procesar notificaciones"
  - "controles de fichas, procesar notificaciones"
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Procesar los mensajes de notificaci&#243;n del control de pesta&#241;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando los usuarios hacen clic en las fichas o los botones, el control de ficha \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\) envía mensajes de notificación a su ventana primaria.  Controle estos mensajes si desea hacer algo en respuesta.  Por ejemplo, cuando el usuario hace clic en una pestaña, quizás desee preestablecer datos de control de la página antes de abrirlo.  
  
 Mensajes de **WM\_NOTIFY** de control de la ficha en la clase de vista o del diálogo.  Utilice la ventana Propiedades para crear una función de controlador de [OnChildNotify](../Topic/CWnd::OnChildNotify.md) con una instrucción switch basada en se manejando qué mensaje de notificación.  Para obtener una lista de las notificaciones que un control de ficha puede enviar a su ventana primaria, vea la sección de **Notificaciones** de [Referencia del Control tab](http://msdn.microsoft.com/library/windows/desktop/bb760548) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)