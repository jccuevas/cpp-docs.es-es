---
title: "COM aislado, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.RegistrarScriptFile"
  - "VC.Project.VCManifestTool.ComponentFileName"
  - "VC.Project.VCManifestTool.TypeLibraryFile"
  - "VC.Project.VCManifestTool.ReplacementsFile"
dev_langs: 
  - "C++"
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM aislado, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este cuadro de diálogo se utiliza para especificar las opciones de **COM aislado** para [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para tener acceso a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades correspondientes al proyecto, o bien la hoja de propiedades.  Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades comunes** y, a continuación, seleccione **COM aislado**.  
  
## Lista de tareas  
  
-   [Cómo: Compilar aplicaciones aisladas que utilicen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## Lista de UIElement  
 **Archivo de biblioteca de tipos**  
 Utiliza la opción \/tlb para especificar el nombre del archivo de biblioteca de tipos \(extensión .tlb\) que la herramienta Manifiesto utilizará para generar el archivo de manifiesto.  
  
 **Archivo de script de registro**  
 Utiliza la opción \/rgs para especificar el nombre del archivo de script de registro \(extensión .rgs\) que la herramienta Manifiesto utilizará para generar el archivo de manifiesto.  
  
 **Nombre de archivo de componente**  
 Utiliza la opción \/dll para especificar el nombre del recurso que generará la herramienta Manifiesto.  Debe especificar un valor para esta propiedad cuando haya especificado valores para **Archivo de biblioteca de tipos** o **Archivo de script de registro**.  
  
 **Archivo de reemplazo**  
 Utiliza la opción \/replacements para especificar la ruta de acceso completa al archivo que contiene valores para las cadenas reemplazables en el archivo .rgs.  
  
## Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Ensamblados en paralelo](_win32_side_by_side_assemblies)   
 [Manifiesto de aplicación ClickOnce](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Herramienta Manifiesto \(Páginas de propiedades\)](../ide/manifest-tool-property-pages.md)   
 [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md)   
 [Cómo: Editar hojas de propiedades de proyecto](../misc/how-to-edit-project-property-sheets.md)