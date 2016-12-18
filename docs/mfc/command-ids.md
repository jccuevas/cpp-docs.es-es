---
title: "Identificadores de comando | Microsoft Docs"
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
  - "identificadores de comando"
  - "identificadores de comando, MFC"
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Identificadores de comando
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El identificador de comando describe un comando totalmente sólo \(codificada en el mensaje de **WM\_COMMAND** \).  Este identificador se asigna al objeto de la interfaz de usuario que genera el comando.  Normalmente, los id. se llama para la funcionalidad del objeto de la interfaz de usuario asignados a.  
  
 Por ejemplo, un elemento claro Todo el menú de edición se puede asignar un identificador como **ID\_EDIT\_CLEAR\_ALL**.  La biblioteca de clases predefine algunos id., especialmente para los comandos que el marco controla propio, como **ID\_EDIT\_CLEAR\_ALL** o `ID_FILE_OPEN`.  Creará otros id. de comando personalmente.  
  
 Cuando crea posee los menús del editor de menús de Visual C\+\+, es una buena idea de seguir la convención de nomenclatura para bibliotecas de clases como se muestra en `ID_FILE_OPEN`.  [Comandos estándar](../mfc/standard-commands.md) explica los comandos estándar definidos por la biblioteca de clases.  
  
## Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)