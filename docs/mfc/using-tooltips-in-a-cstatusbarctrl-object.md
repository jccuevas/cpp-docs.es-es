---
title: Usar informaciones sobre herramientas en un objeto CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442542"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Usar informaciones sobre herramientas en un objeto CStatusBarCtrl

Para habilitar la información sobre herramientas para un control de barra de estado, cree el objeto `CStatusBarCtrl` con el estilo SBT_TOOLTIPS.

> [!NOTE]
>  Si usa un objeto `CStatusBar` para implementar la barra de estado, utilice la función `CStatusBar::CreateEx`. Permite especificar estilos adicionales para el objeto de `CStatusBarCtrl` incrustado.

Una vez que el objeto de `CStatusBarCtrl` se ha creado correctamente, use [CStatusBarCtrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) y [CStatusBarCtrl:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) para establecer y recuperar el texto de sugerencia de un panel específico.

Una vez que se ha establecido la información sobre herramientas, solo se muestra si el elemento tiene un icono y ningún texto, o si no se puede mostrar todo el texto dentro del elemento. No se admiten las sugerencias de herramientas en el modo simple.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
