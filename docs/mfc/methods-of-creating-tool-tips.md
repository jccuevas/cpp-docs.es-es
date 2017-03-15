---
title: "M&#233;todos de creaci&#243;n de informaci&#243;n sobre herramientas | Microsoft Docs"
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
  - "CToolTipCtrl (clase), crear información sobre herramientas"
  - "información sobre herramientas [C++], crear"
  - "información sobre herramientas [C++], controles de información sobre herramientas"
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# M&#233;todos de creaci&#243;n de informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona tres clases para crear y administrar el control de información sobre herramientas: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) y [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md).  Las funciones miembro de información sobre herramientas en estas clases contienen el control común API de Windows.  La clase `CToolBarCtrl` y la clase `CToolTipCtrl` se derivan de la clase `CWnd`.  
  
 `CWnd` proporciona cuatro funciones miembro para crear y administrar información sobre herramientas: [EnableToolTips](../Topic/CWnd::EnableToolTips.md), [CancelToolTips](../Topic/CWnd::CancelToolTips.md), [FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md), y [OnToolHitTest](../Topic/CWnd::OnToolHitTest.md).  Vea estas funciones miembro individual para obtener más información sobre cómo implementar información sobre herramientas.  
  
 Si crea una barra de herramientas mediante `CToolBarCtrl`, puede implementar información sobre herramientas para la barra de herramientas utilizando las siguientes funciones miembro: [GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md) y [SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md).  Vea estas funciones y [Administrar notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md) miembro individual para obtener más información sobre cómo implementar información sobre herramientas.  
  
 La clase de `CToolTipCtrl` proporciona la funcionalidad del control común de información sobre herramientas de Windows.  Un único control de información sobre herramientas puede proporcionar información para más de una herramienta.  Una herramienta es una ventana, como una ventana secundaria o un control, o un área rectangular definido por la aplicación dentro de un área de cliente de ventana.  La clase de [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) deriva de `CToolTipCtrl` y proporciona estilos visuales adicionales y funcionalidad.  
  
## Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)