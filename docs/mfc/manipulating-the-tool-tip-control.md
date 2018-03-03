---
title: "Manipular el Control de información sobre herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae30c39a26379aaa8a6f786b5fe2542abde2c2df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-the-tool-tip-control"></a>Manipular el control de información sobre herramientas
Clase `CToolTipCtrl` proporciona un grupo de miembro funciones que controlan los distintos atributos de la `CToolTipCtrl` objeto y la ventana de información sobre herramientas.  
  
 La inicial, emergente y reshow las duraciones de las ventanas de información sobre herramientas se pueden establecer y recuperar con llamadas a [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) y [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).  
  
 Cambiar la apariencia de las ventanas de información sobre herramientas con las siguientes funciones:  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) y [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) recupera y establece el ancho entre el borde de la sugerencia de herramienta y la herramienta de texto de sugerencia.  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) y [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) recupera y los conjuntos de ventana de información sobre el ancho máximo de la herramienta.  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) y [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) recupera y establece el color de fondo de la herramienta de sugerencia de ventana.  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) y [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) recupera y establece el color del texto de la herramienta de sugerencia de ventana.  
  
 En orden para el control de información sobre herramientas recibir una notificación de mensajes importantes, como **WM_LBUTTONXXX** mensajes, debe transmitir los mensajes para el control de información sobre herramientas. El mejor método para esta retransmisión consiste en realizar una llamada a [CToolTipCtrl:: RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent), en la `PreTranslateMessage` función de la ventana propietaria. En el ejemplo siguiente se muestra un método posible (suponiendo que el control de información sobre herramientas se denomina `m_ToolTip`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 Para quitar inmediatamente una ventana de información sobre herramientas, llame a la [Pop](../mfc/reference/ctooltipctrl-class.md#pop) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

