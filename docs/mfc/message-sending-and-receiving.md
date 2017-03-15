---
title: "Enviar y recibir mensajes | Microsoft Docs"
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
  - "mensajes de notificación de controles"
  - "mensajes [C++], MFC"
  - "mensajes [C++], recibiendo"
  - "mensajes [C++], enviar"
  - "MFC [C++], mensajes"
  - "mensajes de Windows [C++], control de MFC"
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Enviar y recibir mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Considere la parte de envío de proceso y cómo responde el marco.  
  
 La mayoría de los mensajes son el resultado de la interacción del usuario con el programa.  Presiones de tecla de acelerador se generan los comandos por clic del mouse en elementos de menú o botones de la barra de herramientas o.  El usuario también genera mensajes de Windows por, por ejemplo, mover o cambiar el tamaño de una ventana.  Se envían otros mensajes de Windows cuando los eventos como inicio o finalización del programa aparecen, mientras que las ventanas obtienen o pierde el foco, y así sucesivamente.  Los mensajes de la CONTROL\- notificación genera clic del mouse u otras interacciones del usuario con un control, como un botón o un control de cuadro de un cuadro de diálogo.  
  
 La función miembro de **Ejecutar** de la clase `CWinApp` recupera mensajes y los envía a la ventana correspondiente.  La mayoría de los mensajes de comando se envían a la ventana de marco principal de la aplicación.  `WindowProc` predefinido por la biblioteca de clases obtiene los mensajes y los enruta de manera diferente, dependiendo de la categoría de mensaje recibida.  
  
 Ahora considere la parte receptora de proceso.  
  
 El receptor inicial de un mensaje debe ser un objeto de la ventana.  Los mensajes de Windows se administran normalmente directamente por ese objeto de la ventana.  Los mensajes de comando, originando normalmente en la ventana de marco principal de la aplicación, recopile enrutado a la cadena de comando\- destino descrita en [Enrutamiento de comandos](../mfc/command-routing.md).  
  
 Cada objeto capaz de recibir mensajes o comandos tiene su propio tipo asignado que los pares un mensaje o un comando con el nombre del controlador.  
  
 Cuando un objeto de comando\- destino recibe un mensaje o un comando, busca el mapa de mensajes para una coincidencia.  Si encuentra un controlador para el mensaje, llama al controlador.  Para obtener más información sobre cómo se buscan los mapas de mensajes, vea [Cómo el marco busca mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md).  Vea de nuevo a la ilustración [Comandos del marco](../mfc/user-interface-objects-and-command-ids.md).  
  
## Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)