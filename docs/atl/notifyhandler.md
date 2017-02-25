---
title: "NotifyHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NotifyHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NotifyHandler function"
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# NotifyHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El nombre de la función identificada por el tercer parámetro de la macro de `NOTIFY_HANDLER` en el mapa de mensajes.  
  
## Sintaxis  
  
```  
  
      LRESULT   
      NotifyHandler  
      (  
   int idCtrl,  
   LPNMHDR pnmh,  
   BOOL& bHandled   
);  
```  
  
#### Parámetros  
 `idCtrl`  
 El identificador del control que envía el mensaje.  
  
 *pnmh*  
 Dirección de una estructura de [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) que contiene el código de notificación y la información adicional.  Para algunos mensajes de notificación, puntos de este parámetro en una estructura más grande con la estructura de **NMHDR** como primer miembro.  
  
 `bHandled`  
 El mapa de mensajes establece `bHandled` a **TRUE** antes de que se llame a *NotifyHandler* .  Si *NotifyHandler* no controla totalmente el mensaje, debe establecer `bHandled` a **FALSE** para indicar la transformación posterior de las necesidades del mensaje.  
  
## Valor devuelto  
 El resultado del procesamiento de mensajes.  0 si correctamente.  
  
## Comentarios  
 Para obtener un ejemplo de cómo usar este controlador de mensajes en un mapa de mensajes, vea [NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md).  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)