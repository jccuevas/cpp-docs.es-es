---
title: "Procesar notificaciones del control de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), procesar notificaciones"
  - "controles [MFC], encabezado"
  - "notificación de control del encabezado"
  - "controles del encabezado, procesar notificaciones"
  - "notificaciones, procesar para CHeaderCtrl"
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Procesar notificaciones del control de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la clase de vista o del cuadro de diálogo, utilice la ventana Propiedades para crear una función de controlador de [OnChildNotify](../Topic/CWnd::OnChildNotify.md) con una instrucción switch para cualquier mensaje de notificación de encabezado\- CONTROL \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) que desea controlar \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  Las notificaciones se envían a la ventana primaria cuando el usuario hace clic en o haga doble clic en un elemento de encabezado, arrastre un divisor entre los elementos, y así sucesivamente.  
  
 Los mensajes de notificación asociados a un control de encabezado se enumeran en [Referencia del Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775239) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)