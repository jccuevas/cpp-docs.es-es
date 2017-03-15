---
title: "Crear el control de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), crear"
  - "controles del encabezado, crear"
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Crear el control de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control de encabezado no es directamente disponibles en el editor de cuadros de diálogo \(aunque se puede agregar un control de lista, que incluye un control de encabezado\).  
  
### Para colocar un control de encabezado en un cuadro de diálogo  
  
1.  Inserte manualmente una variable miembro de [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) escrito en la clase de diálogo.  
  
2.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), cree y establezca los estilos para `CHeaderCtrl`, colocarlos, y los muestran.  
  
3.  Agregar elementos al control de encabezado.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de diálogo para cualquier mensaje de notificación de encabezado\- CONTROL que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
### Para colocar un control de encabezado en una vista \(no un CListView\)  
  
1.  Inserte un objeto de [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) en la clase de vista.  
  
2.  El estilo, posición, y muestra la ventana de control del encabezado en la función miembro de [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) de la vista.  
  
3.  Agregar elementos al control de encabezado.  
  
4.  Utilice la ventana Propiedades para asignar funciones de controlador en la clase de vista para cualquier mensaje de notificación de encabezado\- CONTROL que necesite controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  
  
 En cualquier caso, se crea el objeto incrustado de control cuando se crea el objeto de vista o del diálogo.  Se debe llamar a [CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md) para crear la ventana de control.  Para colocar el control, la llamada [CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md) para determinar el tamaño inicial del control y para colocar y [SetWindowPos](../Topic/CWnd::SetWindowPos.md) para establecer la posición que desee.  A continuación agregue elementos como se describe en [Agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).  
  
 Para obtener más información, vea [Crear un Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)