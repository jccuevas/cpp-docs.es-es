---
title: "&#191;Puede una aplicaci&#243;n multiproceso tener acceso a un archivo DLL de MFC en distintos subprocesos? | Microsoft Docs"
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
  - "DLL [C++], multithreading"
  - "DLL de MFC [C++], multithreading"
  - "subprocesamiento múltiple [C++], DLL"
  - "subprocesamiento [MFC], DLL"
ms.assetid: e3452e62-021e-4d23-9cce-cff41eb8b46b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#191;Puede una aplicaci&#243;n multiproceso tener acceso a un archivo DLL de MFC en distintos subprocesos?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones multiproceso pueden tener acceso a archivos DLL estándar que se vinculen dinámicamente a MFC y a archivos DLL de extensión de distintos subprocesos.  A partir de la versión 4.2 de Visual C\+\+, una aplicación puede tener acceso a archivos DLL estándar que se vinculen estáticamente a MFC desde varios subprocesos creados en la aplicación.  
  
 Antes de la versión 4.2, sólo se podía asociar un subproceso externo a un archivo DLL estándar vinculado estáticamente a MFC.  Para obtener más información acerca de las restricciones de acceso a archivos DLL estándar vinculados estáticamente a MFC desde varios subprocesos \(antes de la versión 4.2 de Visual C\+\+\), vea el artículo "Multiple Threads and MFC \_USRDLLs" \(Q122676\) de Knowledge Base.  
  
 Tenga en cuenta que en la documentación de Visual C\+\+ ya no se utiliza el término USRDLL.  Un archivo DLL estándar vinculado estáticamente a MFC tiene las mismas características que el antiguo archivo USRDLL.  
  
## Vea también  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)