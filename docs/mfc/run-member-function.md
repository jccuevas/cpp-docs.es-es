---
title: "Run Member (Funci&#243;n) | Microsoft Docs"
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
  - "CWinApp (clase), Run"
  - "suministro de mensajes en CWinApp::Run"
  - "mensajes, bucles"
  - "Run (método), mensajes y procesamiento en inactividad"
  - "WinMain (método)"
  - "WinMain (método), llama a CWinApp::Run"
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Run Member (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación de .NET framework pasa la mayoría del tiempo en la función miembro de [Ejecutar](../Topic/CWinApp::Run.md) de la clase [CWinApp](../mfc/reference/cwinapp-class.md).  Después de la inicialización, `WinMain` llama **Ejecutar** para procesar el bucle de mensajes.  
  
 ciclos de**Ejecutar** a través de un bucle de mensajes, comprobar la cola de mensajes para los mensajes disponibles.  Si un mensaje disponible, **Ejecutar** lo envía para la acción.  Si no hay mensajes, que suele ser true, las llamadas `OnIdle` de **Ejecutar** para realizar cualquier procesamiento en tiempo de inactividad que usted o el marco puede necesitar hecho.  Si no hay mensajes y ningún procesamiento inactivo a hacer, la aplicación espera hasta que ocurra algo.  Cuando la aplicación finaliza, **Ejecutar** llama `ExitInstance`.  La ilustración de [Función miembro de OnIdle](../mfc/onidle-member-function.md) muestra la secuencia de acciones en el bucle de mensajes.  
  
 El envío de mensajes depende de la clase de mensaje.  Para obtener más información, vea [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md).  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)