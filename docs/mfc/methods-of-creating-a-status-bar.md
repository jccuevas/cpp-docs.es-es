---
title: Métodos de creación de una barra de estado
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 9bdaa76dc68467dce1021d9b5f54eaafa248c529
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624269"
---
# <a name="methods-of-creating-a-status-bar"></a>Métodos de creación de una barra de estado

MFC proporciona dos clases para crear barras de estado: [CStatusBar](reference/cstatusbar-class.md) y [CStatusBarCtrl](reference/cstatusbarctrl-class.md) (que incluye la API de control común de Windows). `CStatusBar`proporciona toda la funcionalidad del control común de la barra de estado, interactúa automáticamente con los menús y las barras de herramientas, y controla muchas de las estructuras y configuraciones de control comunes necesarias. sin embargo, el ejecutable resultante será normalmente mayor que el creado con `CStatusBarCtrl` .

`CStatusBarCtrl`normalmente da como resultado un ejecutable más pequeño y es posible que prefiera usar `CStatusBarCtrl` si no desea integrar la barra de estado en la arquitectura de MFC. Si piensa utilizar `CStatusBarCtrl` e integrar la barra de estado en la arquitectura de MFC, debe tener cuidado adicional para comunicar las manipulaciones del control de la barra de estado a MFC. Esta comunicación no es difícil. sin embargo, es un trabajo adicional que no es necesario cuando se usa `CStatusBar` .

Visual C++ proporciona dos maneras de aprovechar el control común de la barra de estado.

- Cree la barra de estado mediante `CStatusBar` y, a continuación, llame a [CStatusBar:: GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl) para obtener acceso a las `CStatusBarCtrl` funciones miembro.

- Cree la barra de estado mediante el constructor de [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

Cualquier método le proporcionará acceso a las funciones miembro del control de barra de estado. Cuando se llama `CStatusBar::GetStatusBarCtrl` a, devuelve una referencia a un `CStatusBarCtrl` objeto, por lo que puede usar cualquier conjunto de funciones miembro. Vea [CStatusBar](reference/cstatusbar-class.md) para obtener información sobre la construcción y creación de una barra de estado mediante `CStatusBar` .

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Permite](controls-mfc.md)
