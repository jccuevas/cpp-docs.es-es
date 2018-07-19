---
title: Inicializar los elementos de un objeto CStatusBarCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89cea1516924530f821003affd96e2848687882b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344349"
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

