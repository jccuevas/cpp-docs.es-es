---
title: Crear un control de cuadro combinado extendido
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: bfc201fbb10c3caa3eaabd0e81206b9493ff7196
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281621"
---
# <a name="creating-an-extended-combo-box-control"></a>Crear un control de cuadro combinado extendido

¿Cómo se crea el control de cuadro combinado extendido depende de si está utilizando el control en un cuadro de diálogo o crearla en una ventana nondialog.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Usar CComboBoxEx directamente en un cuadro de diálogo

1. En el editor de cuadro de diálogo, agregue un control Extended Combo Box al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique cualquier estilo necesario, mediante el cuadro de diálogo Propiedades del control de cuadro combinado extendido.

1. Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CComboBoxEx` funciones miembro.

1. Utilice la ventana Propiedades para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier mensaje de notificación de control de cuadro combinado extendido que necesite controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos adicionales para el `CComboBoxEx` objeto.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Usar CComboBoxEx en una ventana nondialog

1. Defina el control en la clase de vista o la ventana.

1. El control llama [crear](../mfc/reference/ctabctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador. Establecer los estilos para el control.

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)
