---
title: "Controlar y asignar mensajes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "control de mensajes"
  - "mapas de mensajes"
  - "MFC, mensajes"
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controlar y asignar mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta familia de artículo se describe cómo los mensajes y los comandos son procesados por el marco de trabajo de MFC y cómo se conecte el controlador trabaja.  
  
 En los programas tradicionales para Windows, los mensajes de Windows se controlan en una instrucción switch grande en un procedimiento de ventana.  MFC en su lugar utiliza [mapas de mensajes](../mfc/message-categories.md) para asignar mensajes directos a las funciones distintas de miembro de clase.  Los mapas de mensajes son más eficaces que funciones virtuales con este propósito, y permiten que los mensajes se administran mediante la aplicación del objeto más adecuada de C\+\+, documento, vista, y así sucesivamente.  Puede asignar un único mensaje o un intervalo de mensajes, de id. de comando, o de id. del control.  
  
 Los mensajes de**WM\_COMMAND** — generados normalmente por los menús, botones de la barra de herramientas, o los aceleradores — también utilizan el mecanismo de mensaje\- mapa.  MFC define [el enrutamiento](../mfc/command-routing.md) estándar de los mensajes de comando entre la aplicación, la ventana de marco, vista, y los documentos activos en el programa.  Puede invalidar este enrutamiento si necesita.  
  
 Los mapas de mensajes también proporcionan una manera de actualizar objetos de interfaz de usuario \(como menús y botones de la barra de herramientas\), habilitandolos o deshabilitar para adaptarse al contexto actual.  
  
 Para obtener información general sobre los mensajes y colas de mensajes de Windows, vea [Mensajes y colas de mensajes](http://msdn.microsoft.com/library/windows/desktop/ms632590) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [Cómo el marco de trabajo llama a un controlador de mensajes](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [Cómo el marco busca mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [Declarar funciones de controlador de mensajes](../mfc/declaring-message-handler-functions.md)  
  
-   [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [Cómo mostrar la información del comando en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [Actualización dinámica de los objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)  
  
-   [How to: Create a Message Map for a Template \(Clase\)](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CWnd \(clase\)](../mfc/reference/cwnd-class.md)   
 [CCmdTarget Class](../mfc/reference/ccmdtarget-class.md)