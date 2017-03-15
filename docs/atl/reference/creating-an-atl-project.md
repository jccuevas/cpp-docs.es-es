---
title: "Crear un proyecto ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MIN_CRT (macro)"
  - "ATL projects, crear"
  - "ATL70.DLL"
  - "distribuir archivos con componentes ATL"
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Crear un proyecto ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La forma más fácil de crear un proyecto ATL es utilizar el Asistente para proyectos ATL, que se encuentra en la carpeta Proyectos Win32 del **cuadro de diálogo Nuevo proyecto**.  
  
### Para crear un proyecto mediante el Asistente para proyectos ATL  
  
1.  Siga las instrucciones descritas en el tema [Crear un proyecto con un Asistente para aplicaciones de Visual C\+\+](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  Seleccione el icono **Proyecto ATL** en el panel Plantillas para abrir el Asistente para proyectos ATL.  
  
3.  Defina la configuración de la aplicación en la página [Configuración de la aplicación](../../atl/reference/application-settings-atl-project-wizard.md) del `ATL Project Wizard`.  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
4.  Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.  
  
 Cuando haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**.  Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto.  Para obtener más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md).  Para obtener más información acerca de las configuraciones de un nuevo proyecto ATL y cómo cambiarlas, vea [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md).  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)