---
title: "Administrador de automatizaci&#243;n (MFC) | Microsoft Docs"
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
  - "AUTMGR32.exe"
  - "clientes de automatización, administrador de automatización"
  - "administrador de automatización"
  - "servidores de automatización, administrador de automatización"
  - "automatización, administrador de automatización"
  - "automatización remota, administrador de automatización"
ms.assetid: 6bf3429e-1946-41c5-86d0-ad7f5b8585b8
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Administrador de automatizaci&#243;n (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

AUTMGR32.EXE se debe copiar en el directorio system de Windows de cada equipo que se preponiendo proporcionar objetos de automatización remota.  Para Windows 95 y Windows 98, este directorio es normalmente C:\\WINDOWS\\SYSTEM.  Para Windows NT y Windows 2000, es normalmente C:\\WINNT\\SYSTEM32.  
  
 Si desea habilitar devoluciones de llamada del servidor al cliente, este archivo ejecutable también se debe copiar en el directorio system de cada equipo cliente.  
  
 Cuando el administrador de automatización se está ejecutando, se muestra una pequeña ventana en el equipo servidor que contiene la información de estado breve.  Si desea ocultarla, vea el artículo Q138067 en Microsoft Knowledge Base.  
  
## Vea también  
 [Administrador de conexiones de automatización remota](../mfc/remote-automation-connection-manager.md)   
 [Componentes de usuario de automatización remota](../mfc/remote-automation-user-components.md)   
 [Instalación de automatización remota](../mfc/remote-automation-installation.md)