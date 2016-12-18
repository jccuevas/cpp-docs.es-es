---
title: "OnIdle Member (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnIdle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp (clase), OnIdle (método)"
  - "procesamiento de bucles inactivos"
  - "control de mensajes, OnIdle (método)"
  - "OnIdle (método)"
  - "procesar mensajes"
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OnIdle Member (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando no se procesa ningún mensaje de Windows, el marco de trabajo llama a la función [OnIdle](../Topic/CWinApp::OnIdle.md) miembro de [CWinApp](../mfc/reference/cwinapp-class.md) \(descrito en la referencia de la biblioteca MFC\).  
  
 Reemplazo `OnIdle` para realizar tareas en segundo plano.  La versión predeterminada actualiza el estado de los objetos de la interfaz de usuario como botones de la barra de herramientas y realiza la limpieza de los objetos temporales creados por el marco en el curso de sus operaciones.  La ilustración siguiente se muestra cómo el bucle de mensajes llama `OnIdle` cuando no hay mensajes en la cola.  
  
 ![Proceso de bucle de mensajes](../mfc/media/vc387c1.png "vc387C1")  
El bucle de mensajes  
  
 Para obtener más información sobre lo que puede hacer en el bucle de inactividad, vea [Procesamiento de bucles inactivos](../mfc/idle-loop-processing.md).  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)