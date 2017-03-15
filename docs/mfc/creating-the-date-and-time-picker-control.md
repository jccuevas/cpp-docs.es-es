---
title: "Crear el control de selector de fecha y hora | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl (clase), crear"
  - "DateTimePicker (control) [MFC], crear"
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Crear el control de selector de fecha y hora
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cómo se crea un control de selector de fecha y hora depende de si utiliza el control en un cuadro de diálogo o se está realizando en una ventana de nondialog.  
  
### Para utilizar CDateTimeCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadros de diálogo, agregue un Control del selector de fecha y hora al recurso de plantilla de cuadro de diálogo.  Especifique el identificador de control  
  
2.  Especifique cualquier estilo necesario, utilizando el cuadro de diálogo Propiedades del control selector de fecha y hora.  
  
3.  Utilice [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) escrito con la propiedad del Control.  Puede utilizar este miembro para llamar a funciones miembro de `CDateTimeCtrl` .  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de diálogo para cualquier mensaje de [notificación](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) de control selector de fecha y hora que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
5.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), establezca cualquier estilo adicional para el objeto de `CDateTimeCtrl` .  
  
### Para utilizar CDateTimeCtrl en una ventana de nondialog  
  
1.  Declare el control en la vista o la clase de ventana.  
  
2.  Llame a la función miembro de [crear](../Topic/CTabCtrl::Create.md) de control, posiblemente en [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md), posiblemente ya desde la función controladora de [OnCreate](../Topic/CWnd::OnCreate.md) de la ventana primaria \(si está creando subclases el control\).  Establezca los estilos del control.  
  
## Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)