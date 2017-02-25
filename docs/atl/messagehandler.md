---
title: "MessageHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MessageHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MessageHandler function"
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MessageHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**MessageHandler** es el nombre de la función identificada por el segundo parámetro de la macro de `MESSAGE_HANDLER` en el mapa de mensajes.  
  
## Sintaxis  
  
```  
  
      LRESULT   
      MessageHandler  
      (  
   UINT uMsg,  
   WPARAM wParam,  
   LPARAM lParam,  
   BOOL& bHandled  
);  
```  
  
#### Parámetros  
 `uMsg`  
 especifica el mensaje.  
  
 `wParam`  
 Información adicional específica del mensaje.  
  
 `lParam`  
 Información adicional específica del mensaje.  
  
 `bHandled`  
 Se llama a los conjuntos `bHandled` del mapa de mensajes a **TRUE** antes de `MessageHandler` .  Si `MessageHandler` no controla totalmente el mensaje, debe establecer `bHandled` a **FALSO** para indicar que el mensaje necesita un procesamiento adicional.  
  
## Valor devuelto  
 El resultado del procesamiento de mensajes.  0 si correctamente.  
  
## Comentarios  
 Para obtener un ejemplo de cómo usar este controlador de mensajes en un mapa de mensajes, vea [MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md).  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)