---
title: Crear el control de calendario mensual
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 9e430a86c2ac08bde0f031a4c91b9ae5c6f570f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907503"
---
# <a name="creating-the-month-calendar-control"></a>Crear el control de calendario mensual

La forma en que se crea el control de calendario mensual depende de si se usa el control en un cuadro de diálogo o si se crea en una ventana sin cuadro de diálogo.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Para usar CMonthCalCtrl directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de calendario mensual al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique los estilos necesarios mediante el cuadro de diálogo Propiedades del control de calendario mensual.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) con la propiedad del control. Este miembro se puede usar para llamar `CMonthCalCtrl` a funciones miembro.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de notificación del control de calendario mensual que deba controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establezca cualquier otro estilo para el `CMonthCalCtrl` objeto.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Para usar CMonthCalCtrl en una ventana sin cuadro de diálogo

1. Defina el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](../mfc/reference/cmonthcalctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de creación de la ventana primaria (si va a [crear](../mfc/reference/cwnd-class.md#oncreate) una subclase del control). Establezca los estilos del control.

## <a name="see-also"></a>Vea también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
