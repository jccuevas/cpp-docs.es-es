---
title: "P&#225;gina de propiedades NMake | Microsoft Docs"
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
  - "VC.Project.VCNMakeTool.ReBuildCommandLine"
  - "VC.Project.VCNMakeTool.CleanCommandLine"
  - "VC.Project.VCNMakeTool.Output"
  - "VC.Project.VCNMakeTool.BuildCommandLine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMake (página de propiedades)"
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# P&#225;gina de propiedades NMake
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La página de propiedades **NMake** permite especificar la configuración de compilación para proyectos NMake.  
  
 Para obtener más información sobre proyectos NMake, vea [Crear un proyecto de archivos MAKE](../ide/creating-a-makefile-project.md).  
  
 La página de propiedades **NMake** contiene las siguientes propiedades.  
  
## Lista de UIElement  
 **Línea de comandos de Compilar**  
 Especifica el comando que se va a ejecutar cuando se haga clic en **Compilar** en el menú **Compilar**.  
  
 **Línea de comandos de Recompilar todo**  
 Especifica la línea de comandos que se va a ejecutar cuando se haga clic en **Recompilar todo** en el menú **Compilar**.  
  
 **Línea de comandos de Limpiar**  
 Especifica el comando que se va a ejecutar cuando se haga clic en **Limpiar** en el menú **Compilar**.  
  
 **Output**  
 Especifica el nombre del archivo que contendrá los resultados de la línea de comandos.  De manera predeterminada, el nombre de archivo se basa en el nombre del proyecto.  
  
 **Definiciones del preprocesador**  
 Especifica cualquier definición del preprocesador que usa los archivos de origen.  La plataforma y configuración actual determinan el valor predeterminado.  
  
 **Incluir Ruta de búsqueda**  
 Especifica los directorios donde el compilador busca los archivos de inclusión.  
  
 **Archivos de inclusión forzados**  
 Especifica archivos que el preprocesador procesa automáticamente aun cuando no están incluidos en los archivos de proyecto.  
  
 **Ruta de acceso de búsqueda de ensamblado**  
 Especifica los directorios donde .NET Framework busca sus intentos para resolver los ensamblados .NET.  
  
 **Ensamblados de uso forzados**  
 Especifica ensamblados que .NET Framework procesa automáticamente.  
  
 **Opciones adicionales**  
 Especifica cualquier modificador de compilador adicional para que IntelliSense lo utilice cuando analiza archivos C\+\+.  
  
 Para obtener información acerca de cómo tener acceso a la página de propiedades **NMake**, vea [Cómo: Especificar propiedades de proyecto con páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md).  
  
 Para obtener información sobre cómo tener acceso mediante programación a los miembros de este objeto, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.  
  
## Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [Cómo: Habilitar IntelliSense para proyectos de archivos MAKE](../ide/how-to-enable-intellisense-for-makefile-projects.md)