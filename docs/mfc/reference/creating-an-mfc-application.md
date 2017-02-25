---
title: "Crear una aplicaci&#243;n MFC | Microsoft Docs"
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
  - "aplicaciones [MFC]"
  - "MFC [C++], crear aplicaciones"
  - "MFC (aplicaciones)"
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Crear una aplicaci&#243;n MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una aplicación MFC es una aplicación ejecutable para Windows basada en la biblioteca Microsoft Foundation Class \(MFC\).  La forma más fácil de crear una aplicación MFC es utilizar el Asistente para aplicaciones MFC.  
  
> [!IMPORTANT]
>  Los proyectos MFC no se admiten en las ediciones Visual Studio Express.  
  
 Los archivos ejecutables MFC suelen ser de cinco tipos diferentes: aplicaciones para Windows estándar, cuadros de diálogo, aplicaciones basadas en formularios, aplicaciones estilo Explorador de Windows y aplicaciones estilo explorador web.  Para obtener más información, vea:  
  
-   [Utilizar las clases para escribir aplicaciones para Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [Crear y mostrar cuadros de diálogo](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Crear una aplicación MFC basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Crear una aplicación MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [Crear una aplicación MFC estilo explorador web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 El Asistente para aplicaciones MFC generará las clases y los archivos apropiados para estos tipos de aplicaciones, en función de las opciones que seleccione en el asistente.  
  
### Para crear una aplicación MFC mediante el Asistente para aplicaciones MFC  
  
1.  Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C\+\+](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Aplicación MFC**, en el panel Plantillas para abrir el asistente.  
  
3.  Defina la configuración de la aplicación en el [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md).  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
4.  Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.  
  
 Cuando haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**.  Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto.  Para obtener más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## Vea también  
 [Debugging Preparation: Visual C\+\+ Windows Applications](http://msdn.microsoft.com/es-es/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)