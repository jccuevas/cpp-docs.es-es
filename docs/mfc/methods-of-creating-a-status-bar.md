---
title: Métodos de creación de una barra de estado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 784cd7f5768b899388978e6715ff6ca071bf439e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397882"
---
# <a name="methods-of-creating-a-status-bar"></a>Métodos de creación de una barra de estado

MFC proporciona dos clases para crear barras de estado: [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (que encapsula la API del control común de Windows). `CStatusBar` proporciona toda la funcionalidad de la barra de control común de estado, automáticamente interactúa con menús y barras de herramientas y controla muchas de las estructuras y configuración de control comunes necesarios para usted. Sin embargo, el ejecutable resultante normalmente será mayor que creados mediante el uso de `CStatusBarCtrl`.

`CStatusBarCtrl` Normalmente, los resultados en un ejecutable más pequeño y quizás prefiera usar `CStatusBarCtrl` si no va a integrar la barra de estado en la arquitectura MFC. Si tiene previsto usar `CStatusBarCtrl` y la integración de la barra de estado en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones a MFC del control de barra de estado. Esta comunicación no es difícil; Sin embargo, es trabajo adicional que será innecesario cuando usas `CStatusBar`.

Visual C++ proporciona dos maneras de aprovechar el control común de barra de estado.

- Creación de la barra de estado utilizando `CStatusBar`y, a continuación, llame a [CStatusBar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) para obtener acceso a la `CStatusBarCtrl` funciones miembro.

- Creación de la barra de estado utilizando [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)del constructor.

Cualquiera de estos métodos le dará acceso a las funciones miembro de control de la barra de estado. Cuando se llama a `CStatusBar::GetStatusBarCtrl`, devuelve una referencia a un `CStatusBarCtrl` por lo que puede usar cualquier conjunto de funciones miembro de objeto. Consulte [CStatusBar](../mfc/reference/cstatusbar-class.md) para obtener información sobre la construcción y creación de un barra de estado utilizando `CStatusBar`.

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

