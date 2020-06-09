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
ms.openlocfilehash: b010c35f32462810cbdb008e5688d4b41254fad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620771"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo

En algunas aplicaciones, como una aplicación SDI o MDI, querrá insertar un control en una ventana de la aplicación. La función miembro **Create** de la clase contenedora, insertada por Visual C++, puede crear una instancia del control de forma dinámica, sin necesidad de un cuadro de diálogo.

La función miembro **Create** tiene los parámetros siguientes:

*lpszWindowName*<br/>
Puntero al texto que se va a mostrar en la propiedad de texto o título del control (si existe).

*dwStyle*<br/>
Estilos de Windows. Para obtener una lista completa, vea [CWnd:: CreateControl](reference/cwnd-class.md#createcontrol).

*Rect*<br/>
Especifica el tamaño y la posición del control.

*pParentWnd*<br/>
Especifica la ventana primaria del control, normalmente una `CDialog` . No debe ser **null**.

*nID*<br/>
Especifica el identificador de control y puede ser utilizado por el contenedor para hacer referencia al control.

Un ejemplo del uso de esta función para crear dinámicamente un control ActiveX sería en una vista de formulario de una aplicación SDI. Después, podría crear una instancia del control en el `WM_CREATE` controlador de la aplicación.

En este ejemplo, `CMyView` es la clase de vista principal, `CCirc` es la clase contenedora y Circ. H es el encabezado (. H) de la clase contenedora.

La implementación de esta característica es un proceso de cuatro pasos.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Para crear dinámicamente un control ActiveX en una ventana que no sea de cuadro de diálogo

1. Inserte CIRC. H en CMYVIEW. H, justo antes de la `CMyView` definición de clase:

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Agregue una variable miembro (de tipo `CCirc` ) a la sección protegida de la `CMyView` definición de clase ubicada en CMYVIEW. C

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Agregue un `WM_CREATE` controlador de mensajes a la clase `CMyView` .

1. En la función de controlador, `CMyView::OnCreate` , realice una llamada a la función del control `Create` mediante el puntero **this** como ventana primaria:

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Recompile el proyecto. Se creará un control Circ dinámicamente cada vez que se cree la vista de la aplicación.

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](activex-control-containers.md)
