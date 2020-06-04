---
title: Crear un control de cuadro combinado extendido
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907731"
---
# <a name="creating-an-extended-combo-box-control"></a>Crear un control de cuadro combinado extendido

El modo en que se crea el control de cuadro combinado extendido depende de si se usa el control en un cuadro de diálogo o si se crea en una ventana sin cuadro de diálogo.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Para usar CComboBoxEx directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de cuadro combinado extendido al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique los estilos necesarios mediante el cuadro de diálogo Propiedades del control de cuadro combinado extendido.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) con la propiedad del control. Este miembro se puede usar para llamar `CComboBoxEx` a funciones miembro.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de notificación de control de cuadro combinado extendido que deba controlar (consulte [asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establezca cualquier otro estilo para el `CComboBoxEx` objeto.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Para usar CComboBoxEx en una ventana sin cuadro de diálogo

1. Defina el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](../mfc/reference/ctabctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de [creación](../mfc/reference/cwnd-class.md#oncreate) de la ventana primaria. Establezca los estilos del control.

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)
