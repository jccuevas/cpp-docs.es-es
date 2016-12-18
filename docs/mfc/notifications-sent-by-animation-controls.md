---
title: "Notificaciones enviadas por los controles de animaci&#243;n | Microsoft Docs"
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
  - "controles de animación [C++], notificaciones"
  - "CAnimateCtrl (clase), notificaciones"
  - "controles [MFC], animación"
  - "notificaciones, controles de animación"
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Notificaciones enviadas por los controles de animaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de animación \([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)\) envía dos tipos de mensajes de notificación.  Las notificaciones se envían como mensajes de [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) .  
  
 Se envía el mensaje de [ACN\_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) cuando el control de la animación haya iniciado reproducir recorte.  Se envía el mensaje de [ACN\_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) cuando el control de animación ha finalizado o ha dejado de reproducir recorte.  
  
## Vea también  
 [Usar CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Controles](../mfc/controls-mfc.md)