---
title: "Crear un control de cuadro combinado extendido | Microsoft Docs"
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
  - "CComboBoxEx (clase), crear controles de cuadro combinado extendido"
  - "cuadros combinados extendidos"
  - "cuadros combinados extendidos, crear"
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Crear un control de cuadro combinado extendido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cómo se crea el control extendido de cuadro combinado depende de si utiliza el control en un cuadro de diálogo o se está realizando en una ventana de nondialog.  
  
### Para utilizar CComboBoxEx directamente en un cuadro de diálogo  
  
1.  En el editor de cuadros de diálogo, agregue un control combobox extendido el recurso de plantilla de cuadro de diálogo.  Especifique el identificador de control  
  
2.  Especifique cualquier estilo necesario, utilizando el cuadro de diálogo Propiedades del control extendido de cuadro combinado.  
  
3.  Utilice [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) escrito con la propiedad del Control.  Puede utilizar este miembro para llamar a funciones miembro de `CComboBoxEx` .  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de diálogo para cualquier mensaje de notificación extendido de control combobox que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
5.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), establezca cualquier estilo adicional para el objeto de `CComboBoxEx` .  
  
### Para utilizar CComboBoxEx en una ventana de nondialog  
  
1.  Defina el control en la vista o la clase de ventana.  
  
2.  Llame a la función miembro de [crear](../Topic/CTabCtrl::Create.md) de control, posiblemente en [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md), posiblemente ya desde la función controladora de [OnCreate](../Topic/CWnd::OnCreate.md) de la ventana primaria.  Establezca los estilos del control.  
  
## Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)