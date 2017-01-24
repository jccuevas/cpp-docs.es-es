---
title: "Crear un control ActiveX MFC | Microsoft Docs"
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
  - "vc.appwiz.activex.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], crear"
  - "controles ActiveX en MFC [C++], crear"
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un control ActiveX MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los programas de control ActiveX son programas modulares diseñados para ofrecer un tipo específico de funcionalidad a una aplicación primaria.  Por ejemplo, puede crear un control, como un botón, para utilizarlo en un cuadro de diálogo o una barra de herramientas para su uso en una página Web.  
  
 La forma más fácil de crear un control ActiveX de MFC es utilizar el [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).  
  
### Para crear un control ActiveX de MFC mediante el Asistente para controles ActiveX MFC  
  
1.  Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C\+\+](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione el icono **Control ActiveX MFC** en el panel Plantillas para abrir el Asistente para controles ActiveX MFC.  
  
3.  Defina la [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), los [nombres del control](../../mfc/reference/control-names-mfc-activex-control-wizard.md) y la [configuración del control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) mediante el Asistente para controles ActiveX MFC.  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
4.  Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.  
  
 Cuando haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**.  Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto.  Para obtener más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
 Tras haber creado el proyecto, puede utilizar los asistentes para código para agregar [funciones](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [eventos](../../ide/add-event-wizard.md), [propiedades](../../ide/names-add-property-wizard.md) y [métodos](../../ide/add-method-wizard.md).  Para obtener más información sobre cómo personalizar el control ActiveX, vea [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md).  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)