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
ms.openlocfilehash: bd099a67d9f11cc3657a91b4141d3f18c6fa719d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621654"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializar los elementos de un objeto CStatusBarCtrl

De forma predeterminada, una barra de estado muestra información de estado mediante paneles independientes. Estos paneles (también denominados elementos) pueden contener una cadena de texto, un icono o ambos.

Use [SetParts](reference/cstatusbarctrl-class.md#setparts) para definir el número de elementos y la longitud que tendrá la barra de estado. Una vez que haya creado las partes de la barra de estado, realice llamadas a [setText](reference/cstatusbarctrl-class.md#settext) y [SetIcon](reference/cstatusbarctrl-class.md#seticon) para establecer el texto o el icono de una parte específica de la barra de estado. Una vez que el elemento se ha establecido correctamente, el control se vuelve a dibujar automáticamente.

En el ejemplo siguiente se inicializa un `CStatusBarCtrl` objeto existente ( `m_StatusBarCtrl` ) con cuatro paneles y, a continuación, se establece un icono (IDI_ICON1) y un texto en la segunda parte.

[!code-cpp[NVC_MFCControlLadenDialog#31](codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Para obtener más información sobre cómo establecer el modo de un `CStatusBarCtrl` objeto en simple, vea [establecer el modo de un objeto CStatusBarCtrl](setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Permite](controls-mfc.md)
