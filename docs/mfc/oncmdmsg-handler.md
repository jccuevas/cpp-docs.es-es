---
title: "OnCmdMsg (Controlador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnCmdMsg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enrutamiento de comandos, OnCmdMsg (controlador)"
  - "controladores"
  - "controladores, OnCmdMessage"
  - "mensajes, enrutar"
  - "OnCmdMessage (método)"
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OnCmdMsg (Controlador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para realizar el enrutamiento de comandos, cada destino de comando llama a la función miembro de `OnCmdMsg` de destino de comando siguiente en la secuencia.  Los destinos de comando utilizan `OnCmdMsg` para determinar si pueden controlar un comando y distribuirla a otro destino de comando si no pueden controlarlo.  
  
 Cada clase de comando\- destino puede invalidar la función miembro de `OnCmdMsg` .  Reemplaza deje cada clase distribuir comandos a un destino siguiente determinado.  Una ventana de marco, por ejemplo, enruta siempre comandos a la ventana secundaria o vista actual, como se muestra en la tabla [Ruta estándar de comando](../mfc/command-routing.md).  
  
 La implementación predeterminada de `CCmdTarget` de `OnCmdMsg` utiliza el mapa de mensajes de la clase de comando\- destino para buscar una función controladora para cada mensaje de comando que recibe \(de la misma manera que los mensajes estándar que se busca.  Si encuentra una coincidencia, llama al controlador.  La búsqueda de Mensaje\- mapa se explica en [Cómo el marco busca mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md).  
  
## Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)