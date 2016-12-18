---
title: "Trabajar con un control de pesta&#241;a | Microsoft Docs"
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
  - "CTabCtrl (clase), utilizar"
  - "controles de fichas, utilizar"
  - "controles de fichas, trabajar con"
ms.assetid: 819488e3-4944-44b7-9483-195edb8e0aed
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trabajar con un control de pesta&#241;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera más fácil de utilizar un control de ficha \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\) está agregándolo a un recurso de plantilla de cuadro de diálogo con el editor de cuadros de diálogo.  También puede utilizar un control de ficha por sí mismo.  Llamadas **InitCommonControls** MFC para usted.  Las tareas clave son los siguientes:  
  
-   [Crear el control de ficha](../mfc/creating-the-tab-control.md)  
  
-   [Fichas a un control de ficha](../mfc/adding-tabs-to-a-tab-control.md)  
  
-   [Mensajes de notificación del control de ficha de procesamiento](../mfc/processing-tab-control-notification-messages.md)  
  
 Si el objeto de control de la pestaña se inserta en una clase primaria de la vista o de cuadro de diálogo, se destruye el control cuando se destruye el elemento primario.  
  
## Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)