---
title: Crear un control de cuadro combinado extendido
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 554085304f5330ac9cd99a5b814af26ce3a9c7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616284"
---
# <a name="creating-an-extended-combo-box-control"></a>Crear un control de cuadro combinado extendido

El modo en que se crea el control de cuadro combinado extendido depende de si se usa el control en un cuadro de diálogo o si se crea en una ventana sin cuadro de diálogo.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Para usar CComboBoxEx directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de cuadro combinado extendido al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique los estilos necesarios mediante el cuadro de diálogo Propiedades del control de cuadro combinado extendido.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CComboBoxEx](reference/ccomboboxex-class.md) con la propiedad del control. Este miembro se puede usar para llamar a `CComboBoxEx` funciones miembro.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de notificación de control de cuadro combinado extendido que deba controlar (consulte [asignación de mensajes a funciones](reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](reference/cdialog-class.md#oninitdialog), establezca cualquier otro estilo para el `CComboBoxEx` objeto.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Para usar CComboBoxEx en una ventana sin cuadro de diálogo

1. Defina el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](reference/ctabctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de [creación](reference/cwnd-class.md#oncreate) de la ventana primaria. Establezca los estilos del control.

## <a name="see-also"></a>Consulte también

[Uso de CComboBoxEx](using-ccomboboxex.md)<br/>
[Permite](controls-mfc.md)
