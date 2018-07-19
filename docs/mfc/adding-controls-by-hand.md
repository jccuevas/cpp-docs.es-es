---
title: Agregar controles a mano | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39f2d7803630aaaef6e803e90bf332c74937a71
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930620"
---
# <a name="adding-controls-by-hand"></a>Agregar controles a mano
Puede seleccionar [agregar controles a un cuadro de diálogo con el editor de cuadro de diálogo](../mfc/using-the-dialog-editor-to-add-controls.md) o agréguelos usted mismo, con el código.  
  
 Para crear un objeto de control, lo normal sería incrustar el objeto de control de C++ en un cuadro de diálogo de C++ o un objeto de ventana de marco. Al igual que muchos otros objetos en el marco de trabajo, los controles requieren construcción en dos fases. Debe llamar a del control **crear** función de miembro como parte de la creación de la ventana de cuadro o el marco de cuadro de diálogo principal. Para los cuadros de diálogo, esto se hace normalmente en [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)y para las ventanas de marco, en [OnCreate](../mfc/reference/cwnd-class.md#oncreate).  
  
 En el ejemplo siguiente se muestra cómo puede declarar un `CEdit` objeto en la declaración de clase de una clase de cuadro de diálogo derivada y, a continuación, llame a la `Create` función miembro en `OnInitDialog`. Dado que la `CEdit` objeto se declara como un objeto incrustado, se genera automáticamente cuando se construye el objeto de cuadro de diálogo, pero todavía se debe inicializar con su propio `Create` función miembro.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 El siguiente `OnInitDialog` función define un rectángulo, a continuación, llama `Create` para crear el control de edición de Windows y adjuntarlo a la sin inicializar `CEdit` objeto.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 Después de crear el objeto de edición, también puede establecer el foco de entrada al control mediante una llamada a la `SetFocus` función miembro. Por último, se devuelve 0 desde `OnInitDialog` para mostrar que se establece el foco. Si se devuelve un valor distinto de cero, el Administrador de cuadro de diálogo establece el foco en el primer elemento de control de la lista de elementos de cuadro de diálogo. En la mayoría de los casos, deseará agregar controles a los cuadros de diálogo con el editor de cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Crear y utilizar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)   
 [CDialog:: OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

