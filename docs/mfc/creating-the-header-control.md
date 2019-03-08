---
title: Crear el control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 669b13cf566f24bfcd5a29ae41af1cdb90513f73
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326145"
---
# <a name="creating-the-header-control"></a>Crear el control de encabezado

El control de encabezado no está disponible directamente en el editor de cuadro de diálogo (aunque puede agregar un control de lista, que incluye un control de encabezado).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Para colocar un control de encabezado en un cuadro de diálogo

1. Insertar manualmente una variable miembro de tipo [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) en la clase de cuadro de diálogo.

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), crear y establecer los estilos para el `CHeaderCtrl`, colóquelo y mostrarla.

1. Agregar elementos al control de encabezado.

1. Utilice la ventana Propiedades para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier notificación de control de encabezado de los mensajes necesite controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Para colocar un control de encabezado en una vista (no CListView)

1. Incrustar un [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objeto en la clase de vista.

1. Aplicar estilo, posición y mostrar la ventana de control de encabezado en la vista [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función miembro.

1. Agregar elementos al control de encabezado.

1. Utilice la ventana Propiedades para asignar funciones de controlador en la clase de vista para cualquier notificación de control de encabezado de los mensajes necesite controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

En cualquier caso, el objeto de control incrustado se crea cuando se crea el objeto de vista o cuadro de diálogo. A continuación, se debe llamar a [CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create) para crear la ventana de control. Para colocar el control, llame a [CHeaderCtrl:: Layout](../mfc/reference/cheaderctrl-class.md#layout) para determinar el tamaño inicial y la posición del control y [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) para establecer la posición que desee. A continuación, agregar elementos, como se describe en [agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).

Para obtener más información, consulte [creación de un Control de encabezado](/windows/desktop/Controls/header-controls) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
