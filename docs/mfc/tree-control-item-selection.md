---
title: "Selecci&#243;n de elementos de control de &#225;rbol | Microsoft Docs"
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
  - "controles [MFC], seleccionar elementos en"
  - "CTreeCtrl (clase), selección de elementos"
  - "selección de elementos en controles de árbol"
  - "controles de árbol, selección de elementos"
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Selecci&#243;n de elementos de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando cambia la selección de un elemento a otro, un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) envían [TVN\_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) y los mensajes de notificación de [TVN\_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) .  Ambas notificaciones incluyen un valor que especifica si el cambio es el resultado de un clic del mouse o una pulsación de tecla.  Las notificaciones también incluyen información sobre el elemento que se ganando la selección y el elemento que está realizando la selección.  Puede utilizar esta información para establecer los atributos del elemento que dependen del estado de selección del elemento.  Devolver **VERDADERO** en respuesta a **TVN\_SELCHANGING** evita la selección de cambiar; devolver **FALSE** permite el cambio.  
  
 Una aplicación puede cambiar la selección llamando a la función miembro de [SelectItem](../Topic/CTreeCtrl::SelectItem.md) .  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)