---
title: "Mensajes de notificaci&#243;n de controles de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), notificaciones"
  - "mensajes, notificación"
  - "notificaciones, CTreeCtrl"
  - "notificaciones, controles de árbol"
  - "controles de árbol, mensajes de notificación"
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Mensajes de notificaci&#243;n de controles de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) envía los mensajes de notificación siguientes como mensajes de **WM\_NOTIFY** :  
  
|Mensaje de notificación|Descripción|  
|-----------------------------|-----------------|  
|**TVN\_BEGINDRAG**|Señala el inicio de una operación de arrastrar y colocar|  
|**TVN\_BEGINLABELEDIT**|Señala el inicio de la edición en contexto de etiqueta|  
|**TVN\_BEGINRDRAG**|Señala el inicio de una operación de arrastrar y colocar, con el botón secundario del mouse|  
|**TVN\_DELETEITEM**|Señala la eliminación de un elemento específico|  
|**TVN\_ENDLABELEDIT**|Señala el final de la etiqueta|  
|**TVN\_GETDISPINFO**|Solicita información que el control de árbol requiere para mostrar un elemento|  
|**TVN\_ITEMEXPANDED**|Indica que la lista de un elemento primario de elementos secundarios se expande o contrae|  
|**TVN\_ITEMEXPANDING**|Indica que la lista de un elemento primario de elementos secundarios está a punto de ser expandida o contraer|  
|**TVN\_KEYDOWN**|Señala un evento de teclado|  
|**TVN\_SELCHANGED**|Indica que la selección ha cambiado a partir de un elemento a otro|  
|**TVN\_SELCHANGING**|Indica que la selección se va a cambiar a partir de un elemento a otro|  
|**TVN\_SETDISPINFO**|Notificación para actualizar la información mantenida para un elemento|  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)