---
title: "Crear un proyecto de archivos MAKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.makefile.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proyectos de archivos Make, crear"
  - "archivos de proyecto [C++], proyectos de archivos Make"
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un proyecto de archivos MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si tiene un proyecto que se compila desde la línea de comandos con un archivo MAKE, el entorno de desarrollo de Visual Studio no lo reconocerá.  Para abrir y compilar el proyecto mediante [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)], [!INCLUDE[vsPro](../ide/includes/vspro_md.md)] o Visual Studio Express para escritorio de Windows, cree primero un proyecto vacío seleccionando la plantilla de proyecto de archivos MAKE.  Después podrá utilizar este proyecto para compilar el proyecto de archivos MAKE desde el entorno de desarrollo de Visual Studio.  
  
 El proyecto no mostrará ningún archivo en el Explorador de soluciones.  El proyecto especifica la configuración de compilación mostrada en su página de propiedades.  
  
 El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención.  
  
### Para crear un proyecto de archivos MAKE  
  
1.  Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C\+\+](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Proyecto de archivos MAKE** en el panel Plantillas para abrir el asistente.  
  
3.  En la página [Configuración de la aplicación](../ide/application-settings-makefile-project-wizard.md), escriba la información sobre comandos, resultados y limpieza, y la información necesaria para recompilar.  
  
4.  Haga clic en **Finalizar** para cerrar el asistente y abrir el **Explorador de soluciones** del proyecto recién creado.  
  
 Puede ver y editar las propiedades del proyecto en la página de propiedades.  Vea [Establecer las propiedades de un proyecto de Visual C\+\+](../ide/working-with-project-properties.md) para obtener información sobre cómo mostrar la página de propiedades.  
  
## Vea también  
 [Asistente para proyectos de archivo MAKE](../ide/makefile-project-wizard.md)   
 [Caracteres especiales en un archivo MAKE](../build/special-characters-in-a-makefile.md)   
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)