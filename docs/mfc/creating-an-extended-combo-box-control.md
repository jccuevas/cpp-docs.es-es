---
title: Crear un Control de cuadro combinado extendido | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6a891aeadf2fa8366eec52a967e13776db6523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-extended-combo-box-control"></a>Crear un control de cuadro combinado extendido
¿Cómo se crea el control de cuadro combinado extendido depende de si está usando el control en un cuadro de diálogo o crear en una ventana de nondialog.  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Para utilizar CComboBoxEx directamente en un cuadro de diálogo  
  
1.  En el editor de cuadro de diálogo, agregue un control Extended Combo Box para el recurso de plantilla de cuadro de diálogo. Especifique el identificador del control.  
  
2.  Especifique cualquier estilo necesario utilizando el cuadro de diálogo de propiedades del control de cuadro combinado extendido.  
  
3.  Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CComboBoxEx` funciones miembro.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de cuadro de diálogo para cualquier mensaje de notificación del control de cuadro combinado extendido que necesite controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), defina cualquier estilo adicional para el `CComboBoxEx` objeto.  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Para utilizar CComboBoxEx en una ventana de nondialog  
  
1.  Definir el control en la clase de vista o una ventana.  
  
2.  El control de llamada [crear](../mfc/reference/ctabctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador. Establezca los estilos para el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)

