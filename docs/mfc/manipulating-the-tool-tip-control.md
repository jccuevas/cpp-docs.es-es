---
title: Manipular el control de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: d8c994748239871f17b878dd8ea7505a2a8a0b65
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279203"
---
# <a name="manipulating-the-tool-tip-control"></a>Manipular el control de información sobre herramientas

Clase `CToolTipCtrl` proporciona un grupo de miembros de funciones que controlan los distintos atributos de la `CToolTipCtrl` objeto y la ventana de información sobre herramientas.

La inicial, emergente y reshow las duraciones de las ventanas de información sobre herramientas se pueden establecer y recuperar con llamadas a [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) y [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).

Cambiar la apariencia de las ventanas de información sobre herramientas con las siguientes funciones:

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) y [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) recupera y establece el ancho entre el borde de sugerencia de la herramienta y la herramienta de texto de sugerencia.

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) y [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) recupera y conjuntos de ventana de información sobre el ancho máximo de la herramienta.

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) y [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) recupera y establece el color de fondo de la herramienta de sugerencia de ventana.

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) y [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) recupera y establece el color del texto de la herramienta de sugerencia de ventana.

En orden para el control de información sobre herramientas recibir una notificación de mensajes importantes, tales como mensajes WM_LBUTTONXXX, debe transmitir los mensajes para el control de información sobre herramientas. El mejor método para esta transmisión consiste en realizar una llamada a [CToolTipCtrl:: RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent), en el `PreTranslateMessage` función de la ventana propietaria. El ejemplo siguiente muestra un método posible (suponiendo que el control se denomina `m_ToolTip`):

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Para quitar inmediatamente una ventana de información sobre herramientas, llame a la [Pop](../mfc/reference/ctooltipctrl-class.md#pop) función miembro.

## <a name="see-also"></a>Vea también

[Uso de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
