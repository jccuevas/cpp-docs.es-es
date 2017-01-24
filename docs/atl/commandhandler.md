---
title: "CommandHandler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CommandHandler function"
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CommandHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CommandHandler` es la función identificada por el tercer parámetro de la macro de `COMMAND_HANDLER` en el mapa de mensajes.  
  
## Sintaxis  
  
```  
  
      LRESULT   
      CommandHandler  
      (  
   WORD wNotifyCode,  
   WORD wID,  
   HWND hWndCtl,  
   BOOL& bHandled   
);  
```  
  
#### Parámetros  
 `wNotifyCode`  
 El código de notificación.  
  
 *wID*  
 El identificador del elemento de menú, del control, o de aceleradores.  
  
 *hWndCtl*  
 un identificador a un control de la ventana.  
  
 `bHandled`  
 Se llama a los conjuntos `bHandled` del mapa de mensajes a **TRUE** antes de `CommandHandler` .  Si `CommandHandler` no controla totalmente el mensaje, debe establecer `bHandled` a **FALSO** para indicar que el mensaje necesita un procesamiento adicional.  
  
## Valor devuelto  
 El resultado del procesamiento de mensajes.  0 si correctamente.  
  
## Comentarios  
 Para obtener un ejemplo de cómo usar este controlador de mensajes en un mapa de mensajes, vea [COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md).  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)