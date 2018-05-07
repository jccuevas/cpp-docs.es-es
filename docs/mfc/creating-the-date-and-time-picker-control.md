---
title: Crear el Date and Time Picker Control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce7c987bf1284d0287cd0206572209d7ae2d0b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-date-and-time-picker-control"></a>Crear el control de selector de fecha y hora
¿Cómo se crea el control de selector de fecha y hora depende de si está usando el control en un cuadro de diálogo o crear en una ventana de nondialog.  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Para utilizar CDateTimeCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadro de diálogo, agregue un Control Date and Time selector para el recurso de plantilla de cuadro de diálogo. Especifique el identificador del control.  
  
2.  Especifique cualquier estilo necesario utilizando el cuadro de diálogo de propiedades del control de selector de fecha y hora.  
  
3.  Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CDateTimeCtrl` funciones miembro.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de cuadro de diálogo para cualquier control date time picker [notificación](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) mensajes necesarios para controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), defina cualquier estilo adicional para el `CDateTimeCtrl` objeto.  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Para utilizar CDateTimeCtrl en una ventana de nondialog  
  
1.  Declare el control en la clase de vista o una ventana.  
  
2.  El control de llamada [crear](../mfc/reference/ctabctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establezca los estilos para el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

