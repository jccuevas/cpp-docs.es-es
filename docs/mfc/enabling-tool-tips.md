---
title: "Habilitar la informaci&#243;n sobre herramientas | Microsoft Docs"
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
  - "habilitar la información sobre herramientas"
  - "inicializar la información sobre herramientas"
  - "información sobre herramientas [C++], habilitar"
  - "información sobre herramientas [C++], inicializar"
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Habilitar la informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede habilitar la compatibilidad de información sobre herramientas para los controles secundarios de una ventana \(como controles en una vista o un cuadro de diálogo del formulario\).  
  
### Para habilitar la información sobre herramientas de los controles secundarios de una ventana  
  
1.  Llame a `EnableToolTips` para la ventana para la que desea proporcionar información sobre herramientas.  
  
2.  Proporcione una cadena para cada control en el controlador de [Notificación de TTN\_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) .  El controlador está en el mapa de mensajes de la ventana que contiene controles secundarios \(por ejemplo, la clase del formulario\).  Este controlador debe llamar a una función que identifica el control y establezca **pszText** para especificar el texto utilizado por el control de información sobre herramientas.  
  
## Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)