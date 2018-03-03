---
title: Establecer el modo de un objeto CStatusBarCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c954354321d814952ec3ac5ea148cc9177cd0fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Establecer el modo de un objeto CStatusBarCtrl
Existen dos modos para un `CStatusBarCtrl` objeto: simples y no. En la mayoría de los casos, el control de barra de estado tendrá una o varias partes, junto con el texto y quizás un icono o iconos. Esto se le denomina modo. Para obtener más información sobre este modo, vea [inicializar los elementos de un objeto CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Sin embargo, hay casos en que solo tenga que mostrar una sola línea de texto. En este caso, el modo simple es suficiente para sus necesidades. Para cambiar el modo de la `CStatusBarCtrl` objetos en simple, realizar una llamada a la [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) función miembro. Una vez que el control de barra de estado está en modo simple, establecer el texto mediante una llamada a la **SetText** función miembro, pasando 255 como valor para la **nPane** parámetro.  
  
 Puede usar el [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) función para determinar qué modo la `CStatusBarCtrl` objeto se encuentra en.  
  
> [!NOTE]
>  Si se cambia el objeto de barra de estado de no sencilla en simple, o viceversa, la ventana se vuelve a dibujar inmediatamente y, si procede, se restaura automáticamente cualquier parte definida.  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

