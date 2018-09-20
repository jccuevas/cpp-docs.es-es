---
title: Establecer el modo de un objeto CStatusBarCtrl | Microsoft Docs
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
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b398fedb8637ae6ce539a876410222485054919b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409550"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Establecer el modo de un objeto CStatusBarCtrl

Existen dos modos para un `CStatusBarCtrl` objeto: simples y. En la mayoría de los casos, el control de barra de estado tendrá uno o varios elementos, junto con el texto y quizás un icono o iconos. Esto se denomina el modo no simple. Para obtener más información acerca de este modo, consulte [inicializar los elementos de un objeto CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Sin embargo, hay casos donde sólo necesita mostrar una sola línea de texto. En este caso, el modo simple es suficiente para sus necesidades. Para cambiar el modo de la `CStatusBarCtrl` simple de objetos, realizar una llamada a la [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) función miembro. Una vez que el control de barra de estado está en modo simple, establecer el texto mediante una llamada a la `SetText` función miembro, pasando 255 como valor para el *nPane* parámetro.

Puede usar el [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) función para determinar qué modo la `CStatusBarCtrl` objeto se encuentra en.

> [!NOTE]
>  Si se cambia el objeto de barra de estado de no sencilla en simple, o viceversa, la ventana se vuelve a dibujar inmediatamente y, si procede, se restauran automáticamente todas las partes definidas.

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

