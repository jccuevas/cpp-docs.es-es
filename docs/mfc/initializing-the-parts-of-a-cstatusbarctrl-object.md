---
title: Inicializar los elementos de un objeto CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: c813ef53f94fb773b62f102a484eed2be859772e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662168"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializar los elementos de un objeto CStatusBarCtrl

De forma predeterminada, una barra de estado muestra información de estado utilizando paneles distintos. Estos paneles (también denominados elementos) pueden contener una cadena de texto, un icono o ambos.

Use [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para definir el número de elementos y la longitud, tendrá la barra de estado. Después de haber creado las partes de la barra de estado, realizar llamadas a [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) y [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) para establecer el texto o el icono de una parte específica de la barra de estado. Una vez que el elemento se ha establecido correctamente, el control se vuelve a dibujarse automáticamente.

El siguiente ejemplo inicializa existente `CStatusBarCtrl` objeto (`m_StatusBarCtrl`) con cuatro paneles y, a continuación, establece un icono (IDI_ICON1) y algo de texto en la segunda parte.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Para obtener más información sobre cómo establecer el modo de un `CStatusBarCtrl` objeto simple, consulte [establecer el modo de un objeto CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

