---
title: Agregar controles a mano
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: c70539b49fcf2aa87f0bee375a87b38277b6ed42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270766"
---
# <a name="adding-controls-by-hand"></a>Agregar controles a mano

Puede [agregar controles a un cuadro de diálogo con el editor de cuadro de diálogo](../mfc/using-the-dialog-editor-to-add-controls.md) o agréguelos usted mismo, con el código.

Para crear un objeto de control, normalmente insertará el objeto de control de C++ en un cuadro de diálogo de C++ o un objeto de ventana de marco. Al igual que muchos otros objetos en el marco de trabajo, controles requieren construcción en dos fases. Debe llamar a del control **crear** función miembro como parte de la creación de la ventana de cuadro o marco de cuadro de diálogo principal. En los cuadros de diálogo, esto se hace normalmente en [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)y para ventanas de marco en [OnCreate](../mfc/reference/cwnd-class.md#oncreate).

El ejemplo siguiente muestra cómo puede declarar un `CEdit` de objetos en la declaración de clase de una clase derivada de cuadro de diálogo y, a continuación, llame a la `Create` función miembro en `OnInitDialog`. Dado que el `CEdit` objeto se declara como un objeto incrustado, se genera automáticamente cuando se construye el objeto de cuadro de diálogo, pero aún debe inicializarse con su propia `Create` función miembro.

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

La siguiente `OnInitDialog` función configura un rectángulo, a continuación, llama a `Create` para crear el control de edición de Windows y adjuntarla a la no inicializada `CEdit` objeto.

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Después de crear el objeto de edición, también puede establecer el foco de entrada al control mediante una llamada a la `SetFocus` función miembro. Por último, se devuelve 0 desde `OnInitDialog` para mostrar que se establece el foco. Si se devuelve un valor distinto de cero, el Administrador de cuadro de diálogo establece el foco al primer elemento de control en la lista de elementos de cuadro de diálogo. En la mayoría de los casos, deseará agregar controles a los cuadros de diálogo con el editor de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)
