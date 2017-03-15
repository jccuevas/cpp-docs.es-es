---
title: "Administrador de conexiones de automatizaci&#243;n remota | Microsoft Docs"
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
  - "clientes de automatización, configurar para automatización remota"
  - "servidores de automatización, configurar para automatización remota"
  - "Administrador de RAC (herramienta)"
  - "Registro, automatización remota"
  - "Administrador de conexiones de automatización remota"
  - "automatización remota, configurar equipos cliente y servidor"
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Administrador de conexiones de automatizaci&#243;n remota
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para configurar el cliente y los equipos servidor, debe realizar cambios del registro.  En lugar de hacer esto a mano, es mucho más fácil de utilizar la herramienta administrador de Conexión \(RAC\) de automatización remota.  Esta herramienta, RA CMGR32 .EXE, junto con el RA CREG32 .DLL, necesita copiar en cualquier directorio que elija.  Situándola en la PATH, puede ejecutarse desde la barra de tareas utilizando ejecución.  Alternativamente, puede crear un acceso directo a o colocar una referencia a ella en el menú inicio.  
  
 El RA CMGR32 está escrita en Visual Basic y por consiguiente necesita algunos archivos DLL de soporte de Visual Basic.  Estos archivos se colocan en el mismo directorio que el RA CMGR32 .EXE en CD\-ROM.  Las versiones de estos archivos que están instalados por el programa de instalación de Visual C\+\+ Enterprise son equivalentes o más recientes que las que se incluyen con Visual Basic Enterprise Edition 5,0.  Visual C\+\+ configurar copia las nuevas versiones de los archivos de Visual Basic en el directorio del sistema.  Para Windows 9x, este directorio es normalmente C:\\Windows\\System.  Para Windows NT y Windows 2000, es normalmente C:\\WINNT\\system32.  La configuración también registra estos archivos en el sistema operativo.  Puede quitarlos de la instalación de Visual Basic.  
  
## Vea también  
 [Administrador de automatización \(MFC\)](../mfc/automation-manager-mfc.md)   
 [Componentes de usuario de automatización remota](../mfc/remote-automation-user-components.md)   
 [Instalación de automatización remota](../mfc/remote-automation-installation.md)