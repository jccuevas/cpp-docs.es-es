---
title: Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442220"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl

Este es un ejemplo de uso de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Para crear y manipular un CToolTipCtrl

1. Construya el objeto de `CToolTipCtrl`.

1. Llame a [Create](../mfc/reference/ctooltipctrl-class.md#create) para crear el control común de la información sobre herramientas de Windows y adjuntarlo al objeto `CToolTipCtrl`.

1. Llame a [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) para registrar una herramienta con el control de información sobre herramientas, de modo que la información almacenada en la información sobre herramientas se muestre cuando el cursor esté en la herramienta.

1. Llame a [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) para establecer la información que una información sobre herramientas mantiene para una herramienta.

1. Llame a [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) para establecer un nuevo rectángulo delimitador para una herramienta.

1. Llame a [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) para probar un punto y determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así, recupere información sobre la herramienta.

1. Llame a [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) para recuperar un recuento de las herramientas registradas con el control de información sobre herramientas.

## <a name="see-also"></a>Consulte también

[Uso de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
