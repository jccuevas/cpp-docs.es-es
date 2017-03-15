---
title: "Mensajes | Microsoft Docs"
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
  - "mensajes"
  - "mensajes, MFC"
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El bucle de mensajes en la función miembro de **Ejecutar** de la clase `CWinApp` recupera los mensajes en cola generados por varios eventos.  Por ejemplo, cuando el usuario hace clic con el mouse, Windows envía varios mensajes mouse\- relacionados, como `WM_LBUTTONDOWN` cuando se presiona el botón primario y `WM_LBUTTONUP` cuando se suelta el botón primario.  La implementación de bucle de mensajes de la aplicación envía el mensaje a la ventana correspondiente.  
  
 Las categorías principales de mensajes se describen en [Categorías de mensaje](../mfc/message-categories.md).  
  
## Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)