---
title: Manipular el control de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 61bc35e8b19ba7645736b939acac6cdaa6cb7316
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622420"
---
# <a name="manipulating-the-tool-tip-control"></a>Manipular el control de información sobre herramientas

`CToolTipCtrl`La clase proporciona un grupo de funciones miembro que controlan los distintos atributos del `CToolTipCtrl` objeto y la ventana de información sobre herramientas.

Las duraciones iniciales, emergentes y de representación de las ventanas de información sobre herramientas se pueden establecer y recuperar con llamadas a [GetDelayTime](reference/ctooltipctrl-class.md#getdelaytime) y [SetDelayTime](reference/ctooltipctrl-class.md#setdelaytime).

Cambie la apariencia de las ventanas de información sobre herramientas con las siguientes funciones:

- [GetMargin](reference/ctooltipctrl-class.md#getmargin) y [SetMargin](reference/ctooltipctrl-class.md#setmargin) recupera y establece el ancho entre el borde de información sobre herramientas y el texto de información sobre herramientas.

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth) y [SetMaxTipWidth](reference/ctooltipctrl-class.md#setmaxtipwidth) recupera y establece el ancho máximo de la ventana de información sobre herramientas.

- [GetTipBkColor](reference/ctooltipctrl-class.md#gettipbkcolor) y [SetTipBkColor](reference/ctooltipctrl-class.md#settipbkcolor) recupera y establece el color de fondo de la ventana de información sobre herramientas.

- [GetTipTextColor](reference/ctooltipctrl-class.md#gettiptextcolor) y [SetTipTextColor](reference/ctooltipctrl-class.md#settiptextcolor) recupera y establece el color del texto de la ventana de información sobre herramientas.

Para que el control de información sobre herramientas reciba notificaciones de mensajes importantes, como WM_LBUTTONXXX mensajes, debe retransmitir los mensajes al control de información sobre herramientas. El mejor método para esta retransmisión es realizar una llamada a [CToolTipCtrl:: RelayEvent](reference/ctooltipctrl-class.md#relayevent)en la `PreTranslateMessage` función de la ventana propietaria. En el ejemplo siguiente se muestra un método posible (suponiendo que se llama al control de información sobre herramientas `m_ToolTip` ):

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Para quitar inmediatamente una ventana de información sobre herramientas, llame a la función miembro [pop](reference/ctooltipctrl-class.md#pop) .

## <a name="see-also"></a>Consulte también

[Uso de CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Permite](controls-mfc.md)
