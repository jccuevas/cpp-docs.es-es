---
title: Crear el control de pestaña
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619606"
---
# <a name="creating-the-tab-control"></a>Crear el control de pestaña

El modo en que se crea el control de pestaña depende de si se usa el control en un cuadro de diálogo o si se crea en una ventana sin cuadro de diálogo.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Para usar CTabCtrl directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de pestaña al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CTabCtrl](reference/ctabctrl-class.md) con la propiedad del control. Este miembro se puede usar para llamar a `CTabCtrl` funciones miembro.

1. Asigne funciones de controlador en la clase de cuadro de diálogo para los mensajes de notificación del control de pestaña que deba controlar. Para obtener más información, vea [asignar mensajes a funciones](reference/mapping-messages-to-functions.md).

1. En [OnInitDialog](reference/cdialog-class.md#oninitdialog), establezca los estilos para `CTabCtrl` .

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Para usar CTabCtrl en una ventana sin cuadro de diálogo

1. Defina el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](reference/ctabctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de creación de la ventana primaria (si va a [crear](reference/cwnd-class.md#oncreate) una subclase del control). Establezca los estilos del control.

Una vez `CTabCtrl` creado el objeto, puede establecer o borrar los siguientes estilos extendidos:

- **TCS_EX_FLATSEPARATORS** El control de pestaña dibujará separadores entre los elementos de ficha. Este estilo extendido solo afecta a los controles de ficha que tienen los estilos **TCS_BUTTONS** y **TCS_FLATBUTTONS** . De forma predeterminada, al crear el control de pestaña con el estilo **TCS_FLATBUTTONS** se establece este estilo extendido.

- **TCS_EX_REGISTERDROP** El control de pestaña genera **TCN_GETOBJECT** mensajes de notificación para solicitar un objeto de destino de colocación cuando se arrastra un objeto sobre los elementos de ficha del control.

    > [!NOTE]
    >  Para recibir la notificación **TCN_GETOBJECT** , debe inicializar las bibliotecas OLE con una llamada a [AfxOleInit](reference/ole-initialization.md#afxoleinit).

Estos estilos se pueden recuperar y establecer, una vez creado el control, con las llamadas correspondientes a las funciones miembro [GetExtendedStyle](reference/ctabctrl-class.md#getextendedstyle) y [SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle) .

Por ejemplo, establezca el estilo de **TCS_EX_FLATSEPARATORS** con las siguientes líneas de código:

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

Borre el estilo de **TCS_EX_FLATSEPARATORS** de un `CTabCtrl` objeto con las siguientes líneas de código:

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

Se quitarán los separadores que aparecen entre los botones del `CTabCtrl` objeto.

## <a name="see-also"></a>Consulte también

[Uso de CTabCtrl](using-ctabctrl.md)<br/>
[Permite](controls-mfc.md)
