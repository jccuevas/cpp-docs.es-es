---
title: Crear el calendario mensual Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f55960177fa8bc9a31ebfd16b4dbc6aeaba3ee38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

