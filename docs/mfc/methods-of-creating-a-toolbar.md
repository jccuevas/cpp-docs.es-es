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
ms.openlocfilehash: b70e6f4dc15023b878bb58d6b7d0739eeb173d53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624251"
---
# <a name="methods-of-creating-a-toolbar"></a>Métodos de creación de una barra de herramientas

MFC proporciona dos clases para crear barras de herramientas: [CToolBar](reference/ctoolbar-class.md) y [CToolBarCtrl](reference/ctoolbarctrl-class.md) (que incluye la API de control común de Windows). `CToolBar`proporciona toda la funcionalidad del control común de barra de herramientas y controla muchas de las estructuras y configuraciones de control comunes necesarias. sin embargo, el ejecutable resultante será normalmente mayor que el creado con `CToolBarCtrl` .

`CToolBarCtrl`normalmente da como resultado un ejecutable más pequeño y es posible que prefiera usar `CToolBarCtrl` si no desea integrar la barra de herramientas en la arquitectura de MFC. Si tiene previsto utilizar `CToolBarCtrl` e integrar la barra de herramientas en la arquitectura de MFC, debe tener cuidado adicional para comunicar las manipulaciones del control de la barra de herramientas a MFC. Esta comunicación no es difícil. sin embargo, es un trabajo adicional que no es necesario cuando se usa `CToolBar` .

Visual C++ proporciona dos maneras de aprovechar el control común de la barra de herramientas.

- Cree la barra de herramientas mediante `CToolBar` y, a continuación, llame a [CToolBar:: GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl) para obtener acceso a las `CToolBarCtrl` funciones miembro.

- Cree la barra de herramientas mediante el constructor de [CToolBarCtrl](reference/ctoolbarctrl-class.md).

Cualquier método le dará acceso a las funciones miembro del control Toolbar. Cuando se llama `CToolBar::GetToolBarCtrl` a, devuelve una referencia a un `CToolBarCtrl` objeto, por lo que puede usar cualquier conjunto de funciones miembro. Vea [CToolBar](reference/ctoolbar-class.md) para obtener información sobre la construcción y creación de una barra de herramientas con `CToolBar` .

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Permite](controls-mfc.md)
