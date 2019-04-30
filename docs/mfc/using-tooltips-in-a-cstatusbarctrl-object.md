---
title: Usar informaciones sobre herramientas en un objeto CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411440"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Usar informaciones sobre herramientas en un objeto CStatusBarCtrl

Para habilitar informaciones sobre herramientas para un control de barra de estado, cree el `CStatusBarCtrl` objeto con el estilo SBT_TOOLTIPS.

> [!NOTE]
>  Si usas un `CStatusBar` objeto para implementar la barra de estado, use el `CStatusBar::CreateEx` función. Permite especificar estilos adicionales para el objeto incrustado `CStatusBarCtrl` objeto.

Una vez el `CStatusBarCtrl` se ha creado correctamente el objeto, use [CStatusBarCtrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) y [CStatusBarCtrl:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) para establecer y recuperar el texto de sugerencia para un panel específico.

Una vez que se ha establecido la información sobre herramientas, se muestra solo si el elemento tiene un icono y ningún texto, o si no puede mostrarse en la parte de todo el texto. Información sobre herramientas no se admite en el modo simple.

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
