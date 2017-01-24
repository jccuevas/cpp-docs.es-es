---
title: "Manipular el control de informaci&#243;n sobre herramientas | Microsoft Docs"
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
  - "CToolTipCtrl (clase), manipular atributos de información sobre herramientas"
  - "información sobre herramientas [C++], atributos"
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Manipular el control de informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase que `CToolTipCtrl` proporciona un grupo de funciones miembro que controla los distintos atributos del objeto de `CToolTipCtrl` y la ventana de información sobre herramientas.  
  
 La inicial, el elemento emergente, y duraciones de reshow para ventanas de información sobre herramientas se pueden establecer y recuperar con llamadas a [GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md) y a [SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md).  
  
 Cambiar el aspecto de las ventanas de información sobre herramientas con las funciones siguientes:  
  
-   [GetMargin](../Topic/CToolTipCtrl::GetMargin.md) y recupera y conjuntos de [SetMargin](../Topic/CToolTipCtrl::SetMargin.md)el ancho entre el borde de la información sobre herramientas y el texto de información sobre herramientas.  
  
-   [GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md) y recupera y conjuntos de [SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md)el ancho máximo de la ventana de información sobre herramientas.  
  
-   [GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md) y recupera y conjuntos de [SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md)el color de fondo de la ventana de información sobre herramientas.  
  
-   [GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md) y recupera y conjuntos de [SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md)el color del texto de la ventana de información sobre herramientas.  
  
 Para que el control de información sobre herramientas se notifique de mensajes importantes, como los mensajes de **WM\_LBUTTONXXX** , debe retransmitir que los mensajes a la información sobre herramientas controlan.  El mejor método para este retransmitir es realizar una llamada a [CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md), en función de `PreTranslateMessage` de la ventana propietaria.  El ejemplo siguiente se muestra un método posible \(suponiendo que el control de información sobre herramientas se denomina `m_ToolTip`\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/CPP/manipulating-the-tool-tip-control_1.cpp)]  
  
 Para quitar inmediatamente una ventana de información sobre herramientas, llame a la función miembro de [Pop](../Topic/CToolTipCtrl::Pop.md) .  
  
## Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)