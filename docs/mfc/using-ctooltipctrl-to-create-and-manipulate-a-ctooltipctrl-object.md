---
title: Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 186972164496889b471ebfc11e19017129ad943b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378987"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl

Este es un ejemplo de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) uso:

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Para crear y manipular un objeto CToolTipCtrl

1. Construir la `CToolTipCtrl` objeto.

1. Llame a [crear](../mfc/reference/ctooltipctrl-class.md#create) para crear el control común de Windows herramienta tip y adjuntarlo a la `CToolTipCtrl` objeto.

1. Llame a [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) para registrar una herramienta con el control de información sobre herramientas, para que se muestre la información almacenada en la información sobre herramientas cuando el cursor está en la herramienta.

1. Llame a [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) para establecer la información que mantiene una información sobre herramientas para una herramienta.

1. Llame a [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) para establecer un nuevo rectángulo delimitador para una herramienta.

1. Llame a [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) para probar un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así, recuperar información acerca de la herramienta.

1. Llame a [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) recuperar un recuento de las herramientas registrado con el control de información sobre herramientas.

## <a name="see-also"></a>Vea también

[Uso de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

