---
title: "C&#243;mo llegan a los controladores los mensajes que no son de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de mensajes [C++], noncommand (mensajes)"
  - "mensajes [C++], enrutar"
  - "noncommand (mensajes)"
  - "mensajes de Windows [C++], enrutar"
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo llegan a los controladores los mensajes que no son de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A diferencia de comandos, los mensajes estándar de Windows no obtienen enrutado a través de una cadena de comandos pero son administrados normalmente por la ventana a la que Windows envía el mensaje.  La ventana podría ser una ventana de marco principal, una ventana secundaria MDI, un control estándar, cuadro de diálogo, una vista, o alguna otra clase de ventana secundaria.  
  
 En tiempo de ejecución, cada ventana de Windows se asocia a un objeto de la ventana \(se deriva directa o indirectamente de `CWnd`\) que tiene su propio mapa asociado del mensaje y ejecuta el controlador.  El marco de trabajo usa el mapa de mensajes — con respecto a un comando — para asignar mensajes entrantes controladores.  
  
## Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)