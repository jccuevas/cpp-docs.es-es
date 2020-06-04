---
title: Inicializar los elementos de un objeto CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: a5b65a2bbb68eaa7058f3514bb95a5209a0e5e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444456"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializar los elementos de un objeto CStatusBarCtrl

De forma predeterminada, una barra de estado muestra información de estado mediante paneles independientes. Estos paneles (también denominados elementos) pueden contener una cadena de texto, un icono o ambos.

Use [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para definir el número de elementos y la longitud que tendrá la barra de estado. Una vez que haya creado las partes de la barra de estado, realice llamadas a [setText](../mfc/reference/cstatusbarctrl-class.md#settext) y [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) para establecer el texto o el icono de una parte específica de la barra de estado. Una vez que el elemento se ha establecido correctamente, el control se vuelve a dibujar automáticamente.

En el ejemplo siguiente se inicializa un objeto de `CStatusBarCtrl` existente (`m_StatusBarCtrl`) con cuatro paneles y, a continuación, se establece un icono (IDI_ICON1) y texto en la segunda parte.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Para obtener más información sobre cómo establecer el modo de un objeto `CStatusBarCtrl` en simple, vea [establecer el modo de un objeto CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
