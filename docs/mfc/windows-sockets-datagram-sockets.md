---
title: "Windows Sockets: Sockets de datagramas | Microsoft Docs"
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
  - "sockets de datagrama [C++]"
  - "sockets [C++], flujo de datos bidireccional"
  - "sockets [C++], datagrama"
  - "Windows Sockets [C++], flujo de datos bidireccional"
  - "Windows Sockets [C++], datagrama"
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Sockets de datagramas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe los sockets de datagrama, uno de los dos tipos de socket de Windows disponibles. \(El otro tipo es [socket de secuencia](../mfc/windows-sockets-stream-sockets.md).\)  
  
 Los sockets de datagrama admiten un flujo de datos bidireccional que no se garantiza que sea ordenada o para unduplicated.  Los datagramas también no está garantizado que sean confiables; no pueda para proteger.  Los datos de datagrama pueden llegar desordenados y duplicado posiblemente, pero los límites del registro en los datos se conservan, mientras los registros son menores que el límite interno del tamaño del receptor.  Es responsable de la secuencia y la confiabilidad administrar. \(La confiabilidad suele ser buena en redes de área local \[LAN\] solo menos tan en redes de área extendida \[el WAN\], como internet.\)  
  
 Los datagramas se “sines conexión”, es decir, no se establece ninguna conexión explícita; envíe un mensaje de datagrama a un socket especificado y puede recibir mensajes de un socket especificado.  
  
 Un ejemplo de un socket de datagrama es una aplicación que mantiene los relojes del sistema en la red sincronizados.  Esto muestra una capacidad adicional de sockets de datagrama en al menos algunos valores: mensajes de difusión un gran número de direcciones de red.  
  
 Los sockets de datagrama son mejores que los sockets de secuencia para los datos registro\- orientados.  Para obtener más información sobre los sockets de datagrama, vea la especificación de Windows Sockets, disponible en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)