---
title: "Métodos de creación de una barra de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d93f8e43c933e9c8054e798c11754cc48bf54a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-a-toolbar"></a>Métodos de creación de una barra de herramientas
MFC proporciona dos clases para crear barras de herramientas: [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (que ajusta la API del control común de Windows). `CToolBar`proporciona toda la funcionalidad del control común de barra de herramientas, y controla muchas de las estructuras y configuración de control comunes necesaria; Sin embargo, el ejecutable resultante normalmente será mayor que el que creó mediante `CToolBarCtrl`.  
  
 `CToolBarCtrl`Normalmente los resultados en un ejecutable más pequeño así como que prefiera usar `CToolBarCtrl` si no va a integrar la barra de herramientas en la arquitectura de MFC. Si tiene previsto usar `CToolBarCtrl` e integrar la barra de herramientas en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control de barra de herramientas a MFC. Esta comunicación no es difícil; Sin embargo, es una tarea adicional que es innecesaria, cuando se utiliza `CToolBar`.  
  
 Visual C++ proporciona dos formas de aprovechar el control común de barra de herramientas.  
  
-   Crear la barra de herramientas mediante `CToolBar`y, a continuación, llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) para obtener acceso a la `CToolBarCtrl` funciones miembro.  
  
-   Crear la barra de herramientas mediante [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)del constructor.  
  
 Cualquier método permitirá tener acceso a las funciones miembro del control de barra de herramientas. Cuando se llama a `CToolBar::GetToolBarCtrl`, devuelve una referencia a un `CToolBarCtrl` por lo que puede utilizar cualquier conjunto de funciones miembro de objeto. Vea [CToolBar](../mfc/reference/ctoolbar-class.md) para obtener información sobre la construcción y crear una barra de herramientas mediante `CToolBar`.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

