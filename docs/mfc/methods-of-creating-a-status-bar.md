---
title: Métodos de creación de una barra de estado | Documentos de Microsoft
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
ms.openlocfilehash: b0428bfc906ba6e8a1ecc7bd7c198327e8c31505
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346934"
---
# <a name="methods-of-creating-a-status-bar"></a>Métodos de creación de una barra de estado
MFC proporciona dos clases para crear barras de estado: [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (que ajusta la API del control común de Windows). `CStatusBar` proporciona toda la funcionalidad del estado del control común de barra, automáticamente interactúa con menús y barras de herramientas, y controla muchas de las estructuras y configuración de control comunes necesaria; Sin embargo, el ejecutable resultante normalmente será mayor que el que creó mediante `CStatusBarCtrl`.  
  
 `CStatusBarCtrl` Normalmente los resultados en un ejecutable más pequeño así como que prefiera usar `CStatusBarCtrl` si no va a integrar la barra de estado en la arquitectura de MFC. Si tiene previsto usar `CStatusBarCtrl` e integrar la barra de estado en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control MFC de la barra de estado. Esta comunicación no es difícil; Sin embargo, es una tarea adicional que es innecesaria, cuando se utiliza `CStatusBar`.  
  
 Visual C++ proporciona dos formas de aprovechar el control común de barra de estado.  
  
-   Crear la barra de estado utilizando `CStatusBar`y, a continuación, llame a [CStatusBar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) para obtener acceso a la `CStatusBarCtrl` funciones miembro.  
  
-   Crear la barra de estado utilizando [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)del constructor.  
  
 Cualquier método permitirá tener acceso a las funciones miembro del control de barra de estado. Cuando se llama a `CStatusBar::GetStatusBarCtrl`, devuelve una referencia a un `CStatusBarCtrl` por lo que puede utilizar cualquier conjunto de funciones miembro de objeto. Vea [CStatusBar](../mfc/reference/cstatusbar-class.md) para obtener información sobre la construcción y creación de un barra de estado utilizando `CStatusBar`.  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

