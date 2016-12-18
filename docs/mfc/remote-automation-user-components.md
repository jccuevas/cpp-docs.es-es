---
title: "Componentes de usuario de automatizaci&#243;n remota | Microsoft Docs"
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
  - "DLL [C++], automatización"
  - "automatización remota [C++], componentes de usuario"
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Componentes de usuario de automatizaci&#243;n remota
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deberá comprobar que cada equipo cliente contiene el programa cliente y cualquier archivo DLL admiten que requiere.  También necesitará asegurarse de que la aplicación de servidor y cualquier archivo DLL admiten que requiere estén presentes en el equipo servidor.  Finalmente, deberá comprobar que el programa del servidor esté registrado en cada equipo cliente antes de que el administrador de RAC pueda ejecutarse para configurar la conexión.  Si el programa uno mismo\- está registrando \(como la mayoría se\), sólo necesita ejecutar el programa del servidor en el equipo cliente para registrarlo.  Al no encontrarlo, puede tener que ejecutar un archivo de registro suministrado, o modifica manualmente el registro.  
  
## Vea también  
 [Administrador de automatización \(MFC\)](../mfc/automation-manager-mfc.md)   
 [Administrador de conexiones de automatización remota](../mfc/remote-automation-connection-manager.md)   
 [Instalación de automatización remota](../mfc/remote-automation-installation.md)