---
title: Métodos de creación de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 26f31705068df009e906d50451efa9ea6572d7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625455"
---
# <a name="methods-of-creating-tool-tips"></a>Métodos de creación de información sobre herramientas

MFC proporciona tres clases para crear y administrar el control de información sobre herramientas: [CWnd](reference/cwnd-class.md), [CToolBarCtrl](reference/ctoolbarctrl-class.md), [CToolTipCtrl](reference/ctooltipctrl-class.md) y [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md). Las funciones miembro de información sobre herramientas de estas clases incluyen Windows Common control API. La clase `CToolBarCtrl` y la clase `CToolTipCtrl` se derivan de la clase `CWnd` .

`CWnd`proporciona cuatro funciones miembro para crear y administrar la información sobre herramientas: [EnableToolTips](reference/cwnd-class.md#enabletooltips), [CancelToolTips](reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)y [OnToolHitTest](reference/cwnd-class.md#ontoolhittest). Vea estas funciones miembro individuales para obtener más información sobre cómo implementan la información sobre herramientas.

Si crea una barra de herramientas con `CToolBarCtrl` , puede implementar la información sobre herramientas para esa barra de herramientas directamente mediante las siguientes funciones miembro: [GetToolTips](reference/ctoolbarctrl-class.md#gettooltips) y [SetToolTips](reference/ctoolbarctrl-class.md#settooltips). Consulte estas funciones de miembro individuales y control de las [notificaciones de información sobre herramientas](handling-tool-tip-notifications.md) para obtener más información sobre cómo implementan la información sobre herramientas.

La `CToolTipCtrl` clase proporciona la funcionalidad del control de información común de herramientas de Windows. Un único control de información sobre herramientas puede proporcionar información a más de una herramienta. Una herramienta es una ventana, como un control o una ventana secundaria, o un área rectangular definida por la aplicación en el área de cliente de una ventana. La clase [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md) se deriva de `CToolTipCtrl` y proporciona estilos visuales y funcionalidad adicionales.

## <a name="see-also"></a>Consulte también

[Uso de CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Permite](controls-mfc.md)
