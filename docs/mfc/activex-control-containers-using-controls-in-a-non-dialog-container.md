---
title: 'Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: b31581b77743104a92236336c4db380f1693ea55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538793"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo

En algunas aplicaciones, como un SDI o una aplicación MDI, desee incrustar un control en una ventana de la aplicación. El **crear** función miembro de la clase contenedora, insertada por Visual C++, puede crear una instancia del control de forma dinámica, sin necesidad de un cuadro de diálogo.

El **crear** función miembro tiene los siguientes parámetros:

*lpszWindowName*<br/>
Un puntero al texto que se mostrará en la propiedad del control Text o Caption (si existe).

*dwStyle*<br/>
Estilos de Windows. Para obtener una lista completa, consulte [CWnd:: CreateControl](../mfc/reference/cwnd-class.md#createcontrol).

*Rect*<br/>
Especifica el tamaño y la posición del control.

*pParentWnd*<br/>
Especifica la ventana del control primario, normalmente un `CDialog`. No debe ser **NULL**.

*nID*<br/>
Especifica el identificador de control y el contenedor sirve para hacer referencia al control.

Un ejemplo del uso de esta función para crear dinámicamente un control ActiveX sería en una vista de formulario de una aplicación SDI. A continuación, podría crear una instancia del control en el `WM_CREATE` controlador de la aplicación.

En este ejemplo, `CMyView` es la clase de vista principal, `CCirc` es la clase contenedora y CIRC. H es el encabezado (. H) archivo de de la clase contenedora.

Implementación de esta característica es un proceso de cuatro pasos.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Para crear dinámicamente un control ActiveX en una ventana sin cuadro de diálogo

1. Insertar CIRC. H en CMYVIEW. H, justo antes del `CMyView` definición de clase:

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Agregue una variable miembro (de tipo `CCirc`) a la sección protegida de la `CMyView` ubicado en CMYVIEW de definición de clase. H:

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Agregar un `WM_CREATE` controlador de mensajes para la clase `CMyView`.

1. En la función de controlador, `CMyView::OnCreate`, realizar una llamada para el control `Create` funcionan según el **esto** puntero como la ventana primaria:

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Recompile el proyecto. Un control Circ creará dinámicamente cada vez que se crea la vista de la aplicación.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

