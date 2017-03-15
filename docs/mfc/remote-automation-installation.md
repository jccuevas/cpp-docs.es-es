---
title: "Instalaci&#243;n de automatizaci&#243;n remota | Microsoft Docs"
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
  - "instalación de automatización remota"
  - "automatización remota, instalación"
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Instalaci&#243;n de automatizaci&#243;n remota
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Automatización remota tiene relativamente pocos componentes:  
  
-   El proxy de cliente de automatización remota, AUTPRX32.DLL.  
  
-   El componente de servidor de automatización remota, el administrador de automatización, AUTMGR32.EXE.  
  
-   El administrador de RAC, RA CMGR32 .EXE, con el RA coincidente CREG32 .DLL.  
  
 De ellos, escriben en Visual Basic y por consiguiente necesita el administrador de RAC compatibilidad de Visual Basic.  El éstos y otros archivos de automatización remota están instalados por configuración cuando se instala Visual C\+\+ Enterprise Edition.  
  
 Si copia los componentes de automatización remota en un equipo en el que la versión de Visual C\+\+ Enterprise no está instalada, asegúrese de que REGSRV32.EXE está en la ruta de acceso del equipo, y el RA CREG32 .DLL de registro mediante la línea de comandos siguiente:  
  
 REGSRVR32 RA CREG32 .DLL  
  
> [!NOTE]
>  Versiones del administrador de RAC antes de Visual C\+\+ 5,0 GUAGE32.OCX necesarios y TAB CTL32 .OCX.  Ninguno de ellos se requieren para la versión del administrador de RAC que se distribuye con Visual C\+\+ Enterprise, versión 5.0 o posterior.  
  
## En esta sección  
 [El administrador de automatización](../mfc/automation-manager-mfc.md)  
  
 [El administrador de conexiones de automatización remota](../mfc/remote-automation-connection-manager.md)  
  
 [Componentes de automatización remota](../mfc/remote-automation-user-components.md)  
  
## Vea también  
 [Automatización remota](../mfc/remote-automation.md)