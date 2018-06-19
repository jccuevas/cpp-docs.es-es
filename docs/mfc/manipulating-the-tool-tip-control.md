---
title: Manipular el Control de información sobre herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76976c0907d645ad945700c4d396217880712f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346443"
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

