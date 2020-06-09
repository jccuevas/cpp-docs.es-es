---
title: Crear el control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: b08dd4d3f12c70ae495b20b936d44f6a695d1ae1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616242"
---
# <a name="creating-the-header-control"></a>Crear el control de encabezado

El control de encabezado no está directamente disponible en el editor de cuadros de diálogo (aunque puede Agregar un control de lista, que incluye un control de encabezado).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Para colocar un control de encabezado en un cuadro de diálogo

1. Inserte manualmente una variable miembro de tipo [CHeaderCtrl](reference/cheaderctrl-class.md) en la clase de cuadro de diálogo.

1. En [OnInitDialog](reference/cdialog-class.md#oninitdialog), cree y establezca los estilos para `CHeaderCtrl` , colóquelo y muestre.

1. Agregar elementos al control de encabezado.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para los mensajes de notificación de control de encabezado que necesita controlar (consulte [asignación de mensajes a funciones](reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Para colocar un control de encabezado en una vista (no en CListView)

1. Inserte un objeto [CHeaderCtrl](reference/cheaderctrl-class.md) en la clase de vista.

1. Estilo, posición y visualización de la ventana de control de encabezado en la función miembro [OnInitialUpdate](reference/cview-class.md#oninitialupdate) de la vista.

1. Agregar elementos al control de encabezado.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de vista para los mensajes de notificación de control de encabezado que necesita controlar (consulte [asignación de mensajes a funciones](reference/mapping-messages-to-functions.md)).

En cualquier caso, el objeto de control incrustado se crea cuando se crea la vista o el objeto de cuadro de diálogo. A continuación, debe llamar a [CHeaderCtrl:: Create](reference/cheaderctrl-class.md#create) para crear la ventana de control. Para colocar el control, llame a [CHeaderCtrl:: layout](reference/cheaderctrl-class.md#layout) para determinar el tamaño inicial y la posición del control, y [SetWindowPos](reference/cwnd-class.md#setwindowpos) para establecer la posición deseada. A continuación, agregue los elementos como se describe en [Agregar elementos al control de encabezado](adding-items-to-the-header-control.md).

Para obtener más información, vea [crear un control de encabezado](/windows/win32/Controls/header-controls) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Permite](controls-mfc.md)
