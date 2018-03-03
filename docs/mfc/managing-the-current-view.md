---
title: Administrar la vista actual | Documentos de Microsoft
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
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1510b005f452174acfe8ad65ae3f66cf8aafaa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="managing-the-current-view"></a>Administrar la vista actual
Como parte de la implementación predeterminada de ventanas de marco, una ventana de marco realiza un seguimiento de una vista activa. Si la ventana de marco contiene más de una vista, por ejemplo, en una ventana divisora, la vista actual es la vista más reciente en uso. La vista activa es independiente de la ventana activa de Windows o el foco de entrada actual.  
  
 Cuando se cambia la vista activa, el marco de trabajo notifica a la vista actual mediante una llamada a su [OnActivateView](../mfc/reference/cview-class.md#onactivateview) función miembro. Puede indicar si la vista se está activando o desactivando examinando `OnActivateView`del `bActivate` parámetro. De forma predeterminada, `OnActivateView` establece el foco en la vista actual durante la activación. Puede invalidar `OnActivateView` para realizar cualquier procesamiento especial cuando la vista está activado o desactivada. Por ejemplo, puede proporcionar indicaciones visuales especiales para distinguir la vista activa de otras vistas inactivas.  
  
 Una ventana de marco envía comandos a su vista actual (activa), como se describe en [enrutamiento de comandos](../mfc/command-routing.md), junto con el enrutamiento de comandos estándar.  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

