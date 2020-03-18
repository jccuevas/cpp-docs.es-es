---
title: Establecer el modo de un objeto CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446432"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Establecer el modo de un objeto CStatusBarCtrl

Hay dos modos para un objeto `CStatusBarCtrl`: simple y no simple. En la mayoría de los casos, el control de barra de estado tendrá una o más partes, junto con texto y quizás un icono o iconos. Esto se denomina modo no simple. Para obtener más información sobre este modo, vea [inicializar las partes de un objeto CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Sin embargo, hay casos en los que solo necesita mostrar una sola línea de texto. En este caso, el modo simple es suficiente para sus necesidades. Para cambiar el modo del objeto `CStatusBarCtrl` a simple, realice una llamada a la función miembro [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) . Una vez que el control de barra de estado esté en modo simple, establezca el texto mediante una llamada a la función miembro `SetText`, pasando 255 como el valor del parámetro *nPane* .

Puede usar la función [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) para determinar en qué modo se encuentra el objeto de `CStatusBarCtrl`.

> [!NOTE]
>  Si el objeto de barra de estado se está cambiando de no simple a simple, o viceversa, la ventana se vuelve a dibujar inmediatamente y, si es aplicable, se restauran automáticamente los elementos definidos.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
