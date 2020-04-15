---
title: Usar informaciones sobre herramientas en un objeto CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374691"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Usar informaciones sobre herramientas en un objeto CStatusBarCtrl

Para habilitar la información sobre herramientas `CStatusBarCtrl` para un control de barra de estado, cree el objeto con el estilo SBT_TOOLTIPS.

> [!NOTE]
> Si utiliza un `CStatusBar` objeto para implementar la `CStatusBar::CreateEx` barra de estado, utilice la función. Permite especificar estilos adicionales para `CStatusBarCtrl` el objeto incrustado.

Una `CStatusBarCtrl` vez que el objeto se ha creado correctamente, utilice [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) y [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) para establecer y recuperar el texto de sugerencia para un panel específico.

Una vez que se ha establecido la información sobre herramientas, solo se muestra si la pieza tiene un icono y no hay texto, o si todo el texto no se puede mostrar dentro de la pieza. Las sugerencias de herramientas no se admiten en modo simple.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
