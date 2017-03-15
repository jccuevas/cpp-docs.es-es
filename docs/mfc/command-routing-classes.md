---
title: "Clases de enrutamiento de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.command"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enrutamiento de comandos, clases"
  - "MFC, enrutamiento de comandos"
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de enrutamiento de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mientras el usuario interactúa con la aplicación eligiendo menús o los botones de la barra de control con el mouse, la aplicación envía mensajes de objeto afectado de la interfaz de usuario a un objeto del comando\- destino.  Las clases de Comando\- destino derivadas de `CCmdTarget` incluyen [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), y las clases derivadas de ellas.  El marco admite el enrutamiento automático de comando para poder controlar los comandos por el objeto más adecuado actualmente activas en la aplicación.  
  
 Un objeto de clase `CCmdUI` se pasan a los controladores de la interfaz de usuario de comandos de actualización de comando \([ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)\) que permite actualizar el estado de la interfaz de usuario para un comando concreto \(por ejemplo, comprobar o quitar la comprobación de elementos de menú\).  Se llama a las funciones miembro de objetos de `CCmdUI` para actualizar el estado del objeto de interfaz de usuario.  Este proceso es el mismo si el objeto de interfaz de usuario asociada a un comando determinado es un elemento de menú o botón o ambos.  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 Actúa como clase base para todas las clases de objetos que pueden recibir y responder a los mensajes.  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 Proporciona una interfaz de programación para actualizar los objetos de la interfaz de usuario como elementos de menú o botones de barra de control.  El objeto de destino del comando habilita, deshabilita, las comprobaciones, y\/o borra el objeto de la interfaz de usuario con este objeto.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)