---
title: "Tutorial: Implementar una aplicaci&#243;n de Visual C++ en una carpeta local de la aplicaci&#243;n | Microsoft Docs"
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
  - "implementar aplicaciones de Visual C++"
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Implementar una aplicaci&#243;n de Visual C++ en una carpeta local de la aplicaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe cómo implementar una aplicación de Visual C\+\+ copiando los archivos en la carpeta.  
  
## Requisitos previos  
  
-   Un equipo que tiene instalado Visual Studio.  
  
-   Otro equipo que no tenga las bibliotecas de Visual C\+\+.  
  
### Para implementar una aplicación en una carpeta local de la aplicación  
  
1.  Cree y compile una aplicación MFC siguiendo los pasos de [Tutorial: Implementar una aplicación de Visual C\+\+ mediante un proyecto de instalación](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
2.  Copie MFC y la biblioteca adecuados de \(CRT\) en tiempo de ejecución de C archivo \(el archivo para el ejemplo, en una plataforma y Unicode x86 admiten, copie mfc100u.dll y msvcr100.dll de proyectos de \\Program Files\\Microsoft Visual Studio 10.0\\VC\\redist\\x86\\—y a continuación peguelos en la carpeta \\Release\\ del proyecto de MFC.  Para obtener más información sobre otros archivos que es posible que tenga que copiar, vea [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md).  
  
3.  Ejecute la aplicación MFC en un segundo equipo que no tenga las bibliotecas de Visual C\+\+.  
  
    1.  Copie el contenido de \\Release \\ carpeta y péguelos en la carpeta de la aplicación en el segundo equipo.  
  
    2.  Ejecute la aplicación en el segundo equipo.  
  
     La aplicación se ejecuta correctamente porque las bibliotecas de Visual C\+\+ están disponibles en la carpeta de la aplicación local.  
  
## Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)