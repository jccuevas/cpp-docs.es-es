---
title: "Instalación de automatización remota | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation [MFC], installation
- installing Remote Automation [MFC]
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acd8ee55261dfa03c68aef506dc90188d8d27d37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-installation"></a>Instalación de automatización remota
Automatización remota tiene relativamente pocos componentes:  
  
-   El proxy de cliente de automatización remota, AUTPRX32. DLL.  
  
-   La automatización remota componente de servidor, el Administrador de automatización, AUTMGR32. EXE.  
  
-   El Administrador de RAC, RACMGR32. EXE, con su correspondiente RACREG32. DLL.  
  
 De estos, el Administrador de RAC se escribe en Visual Basic y, por tanto, debe admitir el tiempo de ejecución de Visual Basic. Programa de instalación instala estos y otros archivos de automatización remota cuando se instala Visual C++ Enterprise Edition.  
  
 Si copia los componentes de automatización remota a un equipo de la versión de Visual C++ Enterprise Edition no está instalado, asegúrese de que el archivo REGSRV32. EXE se encuentra en la ruta del equipo y registre RACREG32. Archivo DLL mediante la línea de comandos siguiente:  
  
 REGSRVR32 RACREG32. ARCHIVO DLL  
  
> [!NOTE]
>  Las versiones del Administrador de RAC antes de Visual C++ 5.0 requerían los archivos GUAGE32. OCX y TABCTL32. OCX. Ninguna de estas es necesaria para la versión del Administrador de RAC que se incluye con Visual C++ Enterprise Edition, versión 5.0 o posterior.  
  
## <a name="in-this-section"></a>En esta sección  
 [El Administrador de automatización](../mfc/automation-manager-mfc.md)  
  
 [El Administrador de conexiones de automatización remota](../mfc/remote-automation-connection-manager.md)  
  
 [Componentes de usuario de automatización remota](../mfc/remote-automation-user-components.md)  
  
## <a name="see-also"></a>Vea también  
 [Automatización remota](../mfc/remote-automation.md)

