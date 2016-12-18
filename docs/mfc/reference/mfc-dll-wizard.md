---
title: "Asistente para archivos DLL de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.dll.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistente para archivos DLL [MFC]"
  - "DLL [C++], crear"
  - "DLL [C++], MFC"
  - "Asistente para archivos DLL de MFC"
  - "DLL de MFC [C++]"
  - "DLL de MFC [C++], crear"
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para archivos DLL de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando utilice el Asistente para archivos DLL de MFC para crear un proyecto DLL de MFC, obtendrá una aplicación inicial que funciona, con características de funcionalidad integradas que, al compilar, implementarán las características básicas de un archivo [DLL](../../build/dlls-in-visual-cpp.md).  El programa MFC inicial incluye archivos de origen de C\+\+ \(.cpp\), archivos de recursos \(.rc\) y un archivo de proyecto \(.vcxproj\).  El código generado en estos archivos iniciales se basa en MFC.  Para obtener información adicional, vea los detalles del archivo en el archivo Readme.txt que se genera para el proyecto en Visual Studio y [Clases y funciones generadas por el Asistente para archivos DLL de MFC](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md).  
  
## Información general  
 En esta página del asistente se describe la [configuración actual de la aplicación para el proyecto DLL de MFC](../../mfc/reference/application-settings-mfc-dll-wizard.md) que está creando.  De manera predeterminada, se crea el proyecto como un proyecto de archivo DLL estándar \(compartido por MFC\) sin ninguna configuración adicional.  
  
 Para cambiar este comportamiento predeterminado, haga clic en **Configuración de la aplicación**, en la columna izquierda del asistente, y haga los cambios que desee en esa página del Asistente para archivos DLL de MFC.  
  
 Después de crear un proyecto de archivo DLL de MFC, puede agregar objetos o controles al proyecto mediante los [asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md) de Visual C\+\+.  
  
 Puede realizar las tareas y los tipos de mejoras siguientes en un proyecto DLL de MFC básico:  
  
-   [Exportar de un archivo DLL](../../build/exporting-from-a-dll.md)  
  
-   [Vincular un ejecutable a un archivo DLL](../../build/linking-an-executable-to-a-dll.md)  
  
-   [Inicializar un archivo DLL](../../build/initializing-a-dll.md)  
  
## Vea también  
 [Creación y administración de proyectos de Visual C\+\+](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)   
 [MFC \(clase\)](../../mfc/reference/adding-an-mfc-class.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Implementar una interfaz](../../ide/implementing-an-interface-visual-cpp.md)   
 [Compatibilidad del asistente con otros idiomas](../../ide/wizard-support-for-other-languages.md)