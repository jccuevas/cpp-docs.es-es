---
title: Métodos de creación de una barra de herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: 5296c0454e035770e196c3d6a4d15291d0c4ca6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612464"
---
# <a name="methods-of-creating-a-toolbar"></a>Métodos de creación de una barra de herramientas

MFC proporciona dos clases para crear barras de herramientas: [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (que encapsula la API del control común de Windows). `CToolBar` proporciona toda la funcionalidad del control común de barra de herramientas, y controla muchas de las estructuras y configuración de control comunes necesarios para usted. Sin embargo, el ejecutable resultante normalmente será mayor que creados mediante el uso de `CToolBarCtrl`.

`CToolBarCtrl` Normalmente, los resultados en un ejecutable más pequeño y quizás prefiera usar `CToolBarCtrl` si no va a integrar la barra de herramientas en la arquitectura MFC. Si tiene previsto usar `CToolBarCtrl` y la barra de herramientas se integran en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control de barra de herramientas a MFC. Esta comunicación no es difícil; Sin embargo, es trabajo adicional que será innecesario cuando usas `CToolBar`.

Visual C++ proporciona dos maneras de aprovechar el control común de barra de herramientas.

- Cree la barra de herramientas mediante `CToolBar`y, a continuación, llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) para obtener acceso a la `CToolBarCtrl` funciones miembro.

- Cree la barra de herramientas mediante [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)del constructor.

Cualquiera de estos métodos le dará acceso a las funciones miembro del control de barra de herramientas. Cuando se llama a `CToolBar::GetToolBarCtrl`, devuelve una referencia a un `CToolBarCtrl` por lo que puede usar cualquier conjunto de funciones miembro de objeto. Consulte [CToolBar](../mfc/reference/ctoolbar-class.md) para obtener información sobre la construcción y creación de una barra de herramientas mediante `CToolBar`.

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

