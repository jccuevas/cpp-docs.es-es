---
title: "Ejecutar la automatizaci&#243;n remota mediante AUTOCLIK y AUTODRIV | Microsoft Docs"
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
  - "AUTOCLIK (ejemplo) [MFC]"
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ejecutar la automatizaci&#243;n remota mediante AUTOCLIK y AUTODRIV
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

AUTOCLIK es una aplicación de ejemplo simple de servidor de automatización que puede utilizar como base de la que obtener más información sobre la automatización remota.  Es TAMBIÉN una aplicación cliente de automatización que controla AUTOCLIK.  Puede utilizarlas para mostrar la automatización remota.  
  
#### Para instalar AUTOCLIK.EXE en dos equipos y supervisarlo mediante automatización remota  
  
1.  Instale la aplicación de ejemplo de [AUTOCLIK](../top/visual-cpp-samples.md) sobre el equipo de desarrollo.  
  
2.  Compile AUTOCLIK.EXE.  
  
3.  Ejecute AUTOCLIK.EXE en modo independiente y ciérrelo.  Esto se registre como servidor de automatización.  
  
4.  Copie AUTOCLIK.EXE en un equipo remoto, ejecútelo allí, y ciérrelo.  
  
5.  Ejecute AUTODRIV.EXE en el equipo local y compruebe que ejecutándolo inicia AUTOCLIK.EXE.  Para obtener más información sobre AUTODRIV.EXE, vea [AUTOCLIK](../top/visual-cpp-samples.md).  
  
6.  En el equipo remoto, inicie AUTMGR32.EXE \(administrador de automatización\).  
  
7.  En el equipo remoto, inicie el RA CMGR32 .EXE \(administrador de conexiones de automatización remota\).  
  
8.  En el administrador de conexiones de automatización remota, AutoClik.Document seleccione de la lista de **OLE Classes** .  
  
9. Elija una directiva de seguridad del sistema de la ficha de **Acceso de cliente** para conceder acceso de cliente a AutoClik.Document.  
  
10. En el equipo local, el RA CMGR32 .EXE inicial y el AutoClik.Document seleccione de la lista de **OLE Classes** .  
  
11. Desde la ficha de **Conexión de servidor** , elija la dirección de red del equipo remoto y el protocolo de red adecuado.  
  
12. Con AutoClik.Document todavía seleccionado en el cuadro de lista de **OLE Classes** , elija el comando de **Remoto** de menú de `Register` .  
  
13. En el equipo local, ejecute AUTODRIV.EXE o proyecto de equivalente AUTOCLIK.MAK Visual Basic si desea tener Visual Basic, en lugar de MFC, cliente.  
  
 En el equipo remoto, ahora debería poder ver AUTOCLIK que ejecuta los comandos iniciados del cliente local.  
  
## Vea también  
 [Automatización remota](../mfc/remote-automation.md)