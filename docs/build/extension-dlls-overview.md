---
title: "Archivos DLL de extensi&#243;n: informaci&#243;n general | Microsoft Docs"
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
  - "biblioteca AFXDLL"
  - "DLL [C++], extensión"
  - "DLL de extensión [C++], acerca de los archivos DLL de extensión"
  - "DLL de MFC [C++], archivos DLL de extensión"
  - "versiones de DLL compartidas [C++]"
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos DLL de extensi&#243;n: informaci&#243;n general
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un archivo DLL de extensión de MFC es un archivo DLL que implementa clases reutilizables derivadas de clases existentes de la biblioteca MFC \(Microsoft Foundation Class\).  Los archivos DLL de extensión se compilan con la versión de biblioteca de vínculos dinámicos de MFC \(conocida también como la versión compartida de MFC\).  Sólo los archivos ejecutables de MFC \(aplicaciones o archivos DLL estándar\) integrados en la versión compartida de MFC pueden utilizar un archivo DLL de extensión.  Mediante un archivo DLL de extensión, se pueden derivar nuevas clases personalizadas a partir de MFC y ofrecer esta versión extendida de MFC a las aplicaciones que llamen al archivo DLL.  
  
 También se puede utilizar archivos DLL de extensión para realizar transferencias de objetos derivados de MFC entre la aplicación y el archivo DLL.  Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto.  Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, pueden pasarse punteros a objetos de MFC o derivados de MFC con libertad entre una aplicación y los archivos DLL de extensión que cargue.  
  
 Si desea analizar un ejemplo de DLL que satisfaga los requisitos básicos de un archivo DLL de extensión, vea el ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) de MFC.  En concreto, vea los archivos Testdll1.cpp y Testdll2.cpp.  
  
 Tenga en cuenta que en la documentación de Visual C\+\+ ya no se utiliza el término AFXDLL.  Los archivos DLL de extensión tienen las mismas características que los antiguos archivos AFXDLL.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL de extensión](../build/initializing-extension-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL de extensión](../build/extension-dlls.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Archivos DLL que no están basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Crear un archivo DLL compatible con MFC](../mfc/reference/mfc-dll-wizard.md)  
  
## Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)