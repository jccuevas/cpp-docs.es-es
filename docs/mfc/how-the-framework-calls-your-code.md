---
title: "C&#243;mo el marco llama al c&#243;digo | Microsoft Docs"
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
  - "eventos específicos de una aplicación [C++]"
  - "control de comandos, llamar a controladores y código en MFC"
  - "enrutamiento de comandos, marco de trabajo"
  - "enrutamiento de comandos, MFC"
  - "flujo de control [C++], marco de trabajo de MFC y código del usuario"
  - "eventos [C++], enrutamiento de comandos en MFC"
  - "eventos [C++], programación orientada a eventos"
  - "MFC [C++], llamar a código"
  - "MFC [C++], llamar a código desde"
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo el marco llama al c&#243;digo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es crucial comprender la relación entre el código fuente y el marco de trabajo de MFC.  Cuando la aplicación se ejecuta, la mayor parte del flujo de control reside en el código del marco.  El marco de trabajo administra el bucle de mensajes que recibe mensajes de Windows mientras el usuario elige comandos y modifica datos en una vista.  Los eventos que el marco puede administrar en sí mismo no dependen del código en absoluto.  Por ejemplo, el marco sabe cómo cerrar ventanas y salir de la aplicación en respuesta a los comandos de usuario.  Como controla estas tareas, el marco de trabajo usa los controladores de mensajes y las funciones virtuales de C\+\+ para proporcionar posibilidades de responder a estos eventos también.  El código no es en control, sin embargo; el marco de es.  
  
 El marco de trabajo llama al código para los eventos específicos de la aplicación.  Por ejemplo, cuando el usuario elige un comando de menú, el marco distribuye el comando a lo largo de una secuencia de objetos de C\+\+: la ventana de la vista actual y el cuadro, el documento asociado a la vista, la plantilla de documento del documento, y el objeto application.  Si uno de estos objetos puede controlar el comando, lo hace, llamando a la función adecuada del controlador de mensajes.  Para cualquier comando concreto, el código denominado puede ser thes o puede ser el marco.  
  
 Esta organización es algo familiar a los programadores experimentados con la programación tradicional para Windows o programación controlada por eventos.  
  
 En temas relacionados, se leerá lo que hace como se inicializa y ejecuta la aplicación y después limpia el marco mientras la aplicación finaliza.  También entenderá donde el código escribe ajustes en.  
  
 Para obtener más información, vea [Clase CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md) y [Plantillas de documento y el proceso de Creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## Vea también  
 [Compilar en el marco](../mfc/building-on-the-framework.md)