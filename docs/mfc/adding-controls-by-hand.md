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
ms.openlocfilehash: 4efd1c23c7e4d6f7d8e6fa9fe046f8de11c825a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626538"
---
# <a name="adding-controls-by-hand"></a>Agregar controles a mano

Puede [Agregar controles a un cuadro de diálogo con el editor de cuadros de diálogo](using-the-dialog-editor-to-add-controls.md) o agregarlos usted mismo, con código.

Para crear un objeto de control personalmente, normalmente se incrustará el objeto de control de C++ en un cuadro de diálogo de C++ o en un objeto de ventana de marco. Como muchos otros objetos en el marco de trabajo, los controles requieren la construcción en dos fases. Debe llamar a la función miembro **Create** del control como parte de la creación del cuadro de diálogo primario o de la ventana de marco. En los cuadros de diálogo, esto suele hacerse en [OnInitDialog](reference/cdialog-class.md#oninitdialog)y en las ventanas de marco, en [crear](reference/cwnd-class.md#oncreate).

En el ejemplo siguiente se muestra cómo puede declarar un `CEdit` objeto en la declaración de clase de una clase de cuadro de diálogo derivada y, después, llamar a la `Create` función miembro en `OnInitDialog` . Dado que el `CEdit` objeto se declara como un objeto incrustado, se genera automáticamente cuando se construye el objeto de cuadro de diálogo, pero todavía se debe inicializar con su propia `Create` función miembro.

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

La siguiente `OnInitDialog` función configura un rectángulo y, a continuación, llama `Create` a para crear el control de edición de Windows y adjuntarlo al objeto no inicializado `CEdit` .

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Después de crear el objeto de edición, también puede establecer el foco de entrada en el control llamando a la `SetFocus` función miembro. Por último, se devuelve 0 de `OnInitDialog` para mostrar que se ha establecido el foco. Si devuelve un valor distinto de cero, el administrador de cuadros de diálogo establece el foco en el primer elemento de control de la lista de elementos de cuadro de diálogo. En la mayoría de los casos, querrá agregar controles a los cuadros de diálogo con el editor de cuadros de diálogo.

## <a name="see-also"></a>Consulte también

[Creación y uso de controles](making-and-using-controls.md)<br/>
[Permite](controls-mfc.md)<br/>
[CDialog:: OnInitDialog](reference/cdialog-class.md#oninitdialog)
