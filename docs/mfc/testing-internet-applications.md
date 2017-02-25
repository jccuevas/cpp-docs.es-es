---
title: "Probar aplicaciones para Internet | Microsoft Docs"
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
  - "depurar [MFC], aplicaciones web"
  - "depurar aplicaciones web, probar aplicaciones"
  - "probar y depurar en Internet"
  - "pruebas, aplicaciones de Internet"
  - "aplicaciones web, pruebas"
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Probar aplicaciones para Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay algunas dificultades de pruebas en internet, especialmente para las aplicaciones que se ejecutan en un servidor web.  Prueba inicial se lleve probablemente mediante un cliente de usuario único que se conecta a un servidor de pruebas.  Esta opción es útil para depurar el código.  
  
 También deseará probar en condiciones reales: con varios clientes conectados sobre conexiones de alta velocidad así como líneas en serie de la velocidad, incluidas las conexiones del módem.  Puede ser difícil simular condiciones reales, pero está seguro merece la pena dedicar tiempo a diseñado escenarios posibles y que las ejecute.  Si es posible, también deseará utilizar herramientas para hacer capacidad y pruebas de esfuerzo.  Ciertos tipos de errores, como errores de tiempo, son difíciles de encontrar y de reproducir.  
  
 Uno de los temas de programación de internet es su visibilidad.  Muchos métodos al sitio pueden reducir el servidor.  Desea que el servidor reduzcan correctamente.  Desea evitar cualquier cosa que podría ser destructivo a un equipo del usuario si la aplicación \(por ejemplo, daños en los datos mientras escribe en el registro o mientras escribe en cookies en el cliente\).  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)