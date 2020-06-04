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
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365421"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Establecer el modo de un objeto CStatusBarCtrl

Hay dos modos `CStatusBarCtrl` para un objeto: simple y no simple. En la mayoría de los casos, el control de la barra de estado tendrá una o más partes, junto con texto y quizás un icono o iconos. Esto se denomina modo no simple. Para obtener más información sobre este modo, vea [Inicializar las partes de un objeto CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Sin embargo, hay casos en los que solo necesita mostrar una sola línea de texto. En este caso, el modo simple es suficiente para sus necesidades. Para cambiar el `CStatusBarCtrl` modo del objeto a simple, realice una llamada a la [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) función miembro. Una vez que el control de barra de `SetText` estado está en modo simple, establezca el texto llamando a la función miembro, pasando 255 como el valor para el *nPane* parámetro.

Puede utilizar la función [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) `CStatusBarCtrl` para determinar en qué modo se encuentra el objeto.

> [!NOTE]
> Si el objeto de barra de estado se cambia de no simple a simple, o viceversa, la ventana se vuelve a dibujar inmediatamente y, si procede, las partes definidas se restauran automáticamente.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
