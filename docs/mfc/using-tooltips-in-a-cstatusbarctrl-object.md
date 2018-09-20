---
title: Usar informaciones sobre herramientas en un objeto CStatusBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f17dff6680209664e9d029404e4ef012b9f12046
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392364"
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

