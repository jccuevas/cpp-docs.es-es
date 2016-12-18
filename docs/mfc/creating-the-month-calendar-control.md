---
title: "Crear el control de calendario mensual | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl (clase), crear"
  - "controles del calendario mensual"
  - "controles del calendario mensual, crear"
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear el control de calendario mensual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cómo se crea el control de calendario mensual depende de si utiliza el control en un cuadro de diálogo o se está realizando en una ventana de nondialog.  
  
### Para utilizar CMonthCalCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadros de diálogo, agregue un Control de calendario mensual al recurso de plantilla de cuadro de diálogo.  Especifique el identificador de control  
  
2.  Especifique cualquier estilo necesario, utilizando el cuadro de diálogo Propiedades del control de calendario mensual.  
  
3.  Utilice [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) escrito con la propiedad del Control.  Puede utilizar este miembro para llamar a funciones miembro de `CMonthCalCtrl` .  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de diálogo para cualquier mensaje de notificación del control de calendario mensual que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
5.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), establezca cualquier estilo adicional para el objeto de `CMonthCalCtrl` .  
  
### Para utilizar CMonthCalCtrl en una ventana de nondialog  
  
1.  Defina el control en la vista o la clase de ventana.  
  
2.  Llame a la función miembro de [crear](../Topic/CMonthCalCtrl::Create.md) de control, posiblemente en [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md), posiblemente ya desde la función controladora de [OnCreate](../Topic/CWnd::OnCreate.md) de la ventana primaria \(si está creando subclases el control\).  Establezca los estilos del control.  
  
## Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)