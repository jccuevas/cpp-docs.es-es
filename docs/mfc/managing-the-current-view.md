---
title: Administrar la vista actual | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 323903d2e1285a4ee697bbd9d0c3a29c2e1248d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="managing-the-current-view"></a>Administrar la vista actual
Como parte de la implementación predeterminada de ventanas de marco, una ventana de marco realiza un seguimiento de una vista activa. Si la ventana de marco contiene más de una vista, por ejemplo, en una ventana divisora, la vista actual es la vista más reciente en uso. La vista activa es independiente de la ventana activa de Windows o el foco de entrada actual.  
  
 Cuando se cambia la vista activa, el marco de trabajo notifica a la vista actual mediante una llamada a su [OnActivateView](../mfc/reference/cview-class.md#onactivateview) función miembro. Puede indicar si la vista se está activando o desactivando examinando `OnActivateView`del `bActivate` parámetro. De forma predeterminada, `OnActivateView` establece el foco en la vista actual durante la activación. Puede invalidar `OnActivateView` para realizar cualquier procesamiento especial cuando la vista está activado o desactivada. Por ejemplo, puede proporcionar indicaciones visuales especiales para distinguir la vista activa de otras vistas inactivas.  
  
 Una ventana de marco envía comandos a su vista actual (activa), como se describe en [enrutamiento de comandos](../mfc/command-routing.md), junto con el enrutamiento de comandos estándar.  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

