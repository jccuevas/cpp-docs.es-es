---
title: Crear el control de selector de fecha y hora
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: de9baf63577d163b82da1c5977a6ccba6539c73a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907603"
---
# <a name="creating-the-date-and-time-picker-control"></a>Crear el control de selector de fecha y hora

La forma en que se crea el control de selector de fecha y hora depende de si se usa el control en un cuadro de diálogo o si se crea en una ventana sin cuadro de diálogo.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Para usar CDateTimeCtrl directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de selector de fecha y hora al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique los estilos necesarios mediante el cuadro de diálogo Propiedades del control selector de fecha y hora.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) con la propiedad control. Este miembro se puede usar para llamar `CDateTimeCtrl` a funciones miembro.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de [notificación](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) del control selector de fecha y hora que deba controlar (consulte [asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establezca cualquier otro estilo para el `CDateTimeCtrl` objeto.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Para usar CDateTimeCtrl en una ventana sin cuadro de diálogo

1. Declare el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](../mfc/reference/ctabctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de creación de la ventana primaria (si va a [crear](../mfc/reference/cwnd-class.md#oncreate) una subclase del control). Establezca los estilos del control.

## <a name="see-also"></a>Vea también

[Uso de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
