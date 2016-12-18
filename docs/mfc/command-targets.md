---
title: "Destinos de comando | Microsoft Docs"
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
  - "asignación de comandos"
  - "enrutamiento de comandos, destinos de comando"
  - "destinos de comando"
  - "mensajes, comando"
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destinos de comando
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ilustración [Comandos del marco](../mfc/user-interface-objects-and-command-ids.md) muestra la conexión entre un objeto de interfaz de usuario, como un elemento de menú, y la función de controlador que el marco de trabajo llama a para realizar el comando resultante cuando se hace clic en el objeto.  
  
 Windows envía los mensajes que no son mensajes de comando directamente a una ventana cuyo a llamen a controlador del mensaje.  Sin embargo, el marco distribuye los comandos a varios objetos candidatas — “comando denominado destino” — uno de los cuales invoca normalmente un controlador para el comando.  El trabajo de las funciones de controlador de la misma manera para los comandos y los mensajes estándar de Windows, pero los mecanismos mediante los que llaman es diferentes, como se explica en [Cómo el marco de trabajo llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).  
  
## Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)