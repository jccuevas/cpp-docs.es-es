---
title: Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl | Documentos de Microsoft
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
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7f322003a36d89927930c0a57fd060078755f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl
Este es un ejemplo de un uso típico de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Para usar un control de barra de estado con partes  
  
1.  Construir la `CStatusBarCtrl` objeto.  
  
2.  Llame a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si desea establecer el alto mínimo del control de barra de estado del área de dibujo.  
  
3.  Llame a [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) para establecer el color de fondo del control de barra de estado.  
  
4.  Llame a [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para establecer el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.  
  
5.  Llame a [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) para establecer el texto en una parte determinada del control de barra de estado. El mensaje invalida la parte del control que ha cambiado y se muestra el texto nuevo cuando el control siguiente recibe el mensaje `WM_PAINT`.  
  
 En algunos casos, la barra de estado sólo necesita para mostrar una línea de texto. En este caso, realice una llamada a [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Esto coloca el control de barra de estado en modo "simple", que muestra una sola línea de texto.  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

