---
title: "Automatizaci&#243;n en un archivo DLL | Microsoft Docs"
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
  - "automatización [C++], DLL"
  - "DLL [C++], automatización"
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Automatizaci&#243;n en un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando elija la opción de automatización en el Asistente para archivos DLL de MFC, el asistente proporcionará lo siguiente:  
  
-   Un archivo del lenguaje de descripción de objetos \(.ODL\) de inicio  
  
-   Una directiva de inclusión en el archivo STDAFX.h para Afxole.h  
  
-   Una implementación de la función `DllGetClassObject`, que llama a la función **AfxDllGetClassObject**  
  
-   Una implementación de la función `DllCanUnloadNow`, que llama a la función **AfxDllCanUnloadNow**  
  
-   Una implementación de la función `DllRegisterServer`, que llama a la función [COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Servidores de automatización](../mfc/automation-servers.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)