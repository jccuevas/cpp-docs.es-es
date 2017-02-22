---
title: "Crear un proyecto DLL de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcdll.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], crear"
  - "DLL [C++], MFC"
  - "DLL de MFC [C++], crear proyectos"
  - "proyectos [C++], crear"
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Crear un proyecto DLL de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un archivo DLL de MFC es un archivo binario que actúa como una biblioteca compartida de funciones que pueden utilizar simultáneamente varias aplicaciones.  La forma más fácil de crear un proyecto DLL de MFC es utilizar el Asistente para archivos DLL de MFC.  
  
> [!NOTE]
>  Las características del IDE pueden depender de la edición o configuración activa, y ser diferentes de las que se describen en la Ayuda.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para crear un proyecto DLL de MFC mediante el Asistente para archivos DLL de MFC  
  
1.  Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C\+\+](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
 **Nota** En el cuadro de diálogo **Nuevo proyecto**, seleccione el icono `MFC DLL` en el panel Plantillas para abrir el Asistente para archivos DLL de MFC.  
  
1.  Defina la configuración de la aplicación en la página [configuración de la aplicación](../../mfc/reference/application-settings-mfc-dll-wizard.md) del [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md).  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
2.  Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el **Explorador de soluciones**.  
  
 Cuando haya creado el proyecto, podrá ver los archivos creados en el Explorador de soluciones.  Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto.  Para obtener más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## Vea también  
 [Tipos de proyecto de Visual C\+\+](../Topic/Debugging%20Preparation:%20Visual%20C++%20Project%20Types.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)