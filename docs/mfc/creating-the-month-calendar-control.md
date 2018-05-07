---
title: Crear el calendario mensual Control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e5cb58cfbecd03964963814081c2f0039c0752c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-month-calendar-control"></a>Crear el control de calendario mensual
¿Cómo se crea el control de calendario mensual depende de si está usando el control en un cuadro de diálogo o crear en una ventana de nondialog.  
  
### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Para utilizar CMonthCalCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadro de diálogo, agregue un Control de calendario mensual para el recurso de plantilla de cuadro de diálogo. Especifique el identificador del control.  
  
2.  Especifique cualquier estilo necesario utilizando el cuadro de diálogo de propiedades del control de calendario mensual.  
  
3.  Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CMonthCalCtrl` funciones miembro.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de cuadro de diálogo para cualquier notificación de control de calendario de mes de los mensajes necesite controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), defina cualquier estilo adicional para el `CMonthCalCtrl` objeto.  
  
### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Para utilizar CMonthCalCtrl en una ventana de nondialog  
  
1.  Definir el control en la clase de vista o una ventana.  
  
2.  El control de llamada [crear](../mfc/reference/cmonthcalctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establezca los estilos para el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)

