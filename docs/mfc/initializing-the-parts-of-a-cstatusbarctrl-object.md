---
title: Inicializar los elementos de un objeto CStatusBarCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b713a46db13508df5ba80b21e3dfe938261eec65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializar los elementos de un objeto CStatusBarCtrl
De forma predeterminada, una barra de estado muestra información de estado utilizando paneles distintos. Estos paneles (también denominados partes) pueden contener una cadena de texto, un icono o ambos.  
  
 Use [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para definir el número de elementos y la longitud, tendrá la barra de estado. Después de haber creado los elementos de la barra de estado, realizar llamadas a [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) y [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) para establecer el texto o icono de una parte específica de la barra de estado. Una vez que el elemento se ha establecido correctamente, el control se vuelve a dibujarse automáticamente.  
  
 En el ejemplo siguiente se inicializa existente `CStatusBarCtrl` objeto (`m_StatusBarCtrl`) con cuatro paneles y, a continuación, establece un icono (IDI_ICON1) y algo de texto en la segunda parte.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 Para obtener más información acerca de cómo establecer el modo de un `CStatusBarCtrl` objeto a simple, vea [establecer el modo de un objeto CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

