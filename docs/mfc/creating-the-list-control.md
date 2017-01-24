---
title: "Crear el control de lista | Microsoft Docs"
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
  - "CListCtrl (clase), crear control"
  - "controles de lista"
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear el control de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cómo se crea el control de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\) depende de si utiliza el control directamente o utiliza la clase [CListView](../mfc/reference/clistview-class.md) en su lugar.  Si utiliza `CListView`, crea el marco de vista como parte de la secuencia de creación de documentos y vistas.  Crear la vista de lista hace que el control de lista también \(los dos son lo mismo\).  El control se crea en la función de controlador de [OnCreate](../Topic/CWnd::OnCreate.md) de la vista.  En este caso, el control está listo para agregar elementos, mediante una llamada a [GetListCtrl](../Topic/CListView::GetListCtrl.md).  
  
### Para utilizar CListCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadros de diálogo, agregue un control de lista al recurso de plantilla de cuadro de diálogo.  Especifique el identificador de control  
  
2.  Utilice [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de `CListCtrl` escrito con la propiedad del Control.  Puede utilizar este miembro para llamar a funciones miembro de `CListCtrl` .  
  
3.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de diálogo para cualquier mensaje de notificación del control de lista que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
4.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), establezca los estilos para `CListCtrl`.  Vea [Cambiar los estilos del control de lista](../mfc/changing-list-control-styles.md).  Determina la clase “vista” recopilados en el control, aunque puede cambiar la vista más adelante.  
  
### Para utilizar CListCtrl en una ventana de nondialog  
  
1.  Defina el control en la vista o la clase de ventana.  
  
2.  Llame a la función miembro de [crear](../Topic/CListCtrl::Create.md) de control, posiblemente en [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md), posiblemente ya desde la función controladora de [OnCreate](../Topic/CWnd::OnCreate.md) de la ventana primaria \(si está creando subclases el control\).  Establezca los estilos del control.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)