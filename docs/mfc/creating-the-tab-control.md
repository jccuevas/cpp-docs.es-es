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
ms.openlocfilehash: 4627009e2e07d1c5692d83d8d6262a9fcd37977e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241967"
---
# <a name="creating-the-tab-control"></a>Crear el control de pestaña

¿Cómo se crea el control de ficha depende de si está utilizando el control en un cuadro de diálogo o crearla en una ventana nondialog.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Usar CTabCtrl directamente en un cuadro de diálogo

1. En el editor de cuadro de diálogo, agregue un Control de ficha al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CTabCtrl](../mfc/reference/ctabctrl-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CTabCtrl` funciones miembro.

1. Asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de notificación de control de ficha que debe controlar. Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos para el `CTabCtrl`.

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Usar CTabCtrl en una ventana nondialog

1. Defina el control en la clase de vista o la ventana.

1. El control llama [crear](../mfc/reference/ctabctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establecer los estilos para el control.

Después de la `CTabCtrl` se ha creado el objeto, puede establecer o borrar los siguientes estilos extendidos:

- **TCS_EX_FLATSEPARATORS** el control de ficha dibuja separadores entre los elementos de ficha. Este estilo extendido solo afecta a la pestaña controles que tienen la **TCS_BUTTONS** y **TCS_FLATBUTTONS** estilos. De forma predeterminada, la creación del control de ficha con la **TCS_FLATBUTTONS** estilo establece este estilo extendido.

- **TCS_EX_REGISTERDROP** genera el control de ficha **TCN_GETOBJECT** mensajes de notificación para solicitar un destino de colocación de objetos cuando se arrastra un objeto a través de los elementos de ficha en el control.

    > [!NOTE]
    >  Para recibir el **TCN_GETOBJECT** notificación, debe inicializar las bibliotecas OLE con una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

Estos estilos se pueden recuperar y establecer una vez creado el control, con llamadas a la [funciones miembro GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) y [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) funciones miembro.

Por ejemplo, establecer el **TCS_EX_FLATSEPARATORS** estilo con las siguientes líneas de código:

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

Desactive el **TCS_EX_FLATSEPARATORS** estilo con un `CTabCtrl` objeto con las siguientes líneas de código:

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

Esto quitará los separadores que aparecen entre los botones de su `CTabCtrl` objeto.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
