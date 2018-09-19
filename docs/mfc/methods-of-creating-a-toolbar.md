---
title: Métodos de creación de una barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052f1578386746f9a4d9892576f09b3b61547289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348640"
---
# <a name="methods-of-creating-a-toolbar"></a>Métodos de creación de una barra de herramientas
MFC proporciona dos clases para crear barras de herramientas: [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (que ajusta la API del control común de Windows). `CToolBar` proporciona toda la funcionalidad del control común de barra de herramientas, y controla muchas de las estructuras y configuración de control comunes necesaria; Sin embargo, el ejecutable resultante normalmente será mayor que el que creó mediante `CToolBarCtrl`.  
  
 `CToolBarCtrl` Normalmente los resultados en un ejecutable más pequeño así como que prefiera usar `CToolBarCtrl` si no va a integrar la barra de herramientas en la arquitectura de MFC. Si tiene previsto usar `CToolBarCtrl` e integrar la barra de herramientas en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control de barra de herramientas a MFC. Esta comunicación no es difícil; Sin embargo, es una tarea adicional que es innecesaria, cuando se utiliza `CToolBar`.  
  
 Visual C++ proporciona dos formas de aprovechar el control común de barra de herramientas.  
  
-   Crear la barra de herramientas mediante `CToolBar`y, a continuación, llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) para obtener acceso a la `CToolBarCtrl` funciones miembro.  
  
-   Crear la barra de herramientas mediante [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)del constructor.  
  
 Cualquier método permitirá tener acceso a las funciones miembro del control de barra de herramientas. Cuando se llama a `CToolBar::GetToolBarCtrl`, devuelve una referencia a un `CToolBarCtrl` por lo que puede utilizar cualquier conjunto de funciones miembro de objeto. Vea [CToolBar](../mfc/reference/ctoolbar-class.md) para obtener información sobre la construcción y crear una barra de herramientas mediante `CToolBar`.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

