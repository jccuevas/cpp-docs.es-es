---
title: "Avanzadas, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.KeyFile"
  - "VC.Project.VCManifestTool.UpdateFileHashes"
  - "VC.Project.VCManifestTool.UpdateFileHashesSearchPath"
  - "VC.Project.VCManifestTool.ValidateSignature"
  - "VC.Project.VCManifestTool.KeyContainer"
dev_langs: 
  - "C++"
ms.assetid: 3d587366-05ea-4956-a978-313069660735
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Avanzadas, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este cuadro de diálogo se utiliza para especificar las opciones avanzadas de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para tener acceso a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades correspondientes al proyecto, o bien la hoja de propiedades.  Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades de configuración** y, a continuación, seleccione **Avanzadas**.  
  
## Lista de UIElement  
 **Actualizar hash de archivo**  
 Utiliza la opción \/hashupdate para especificar que la herramienta Manifiesto calculará los valores hash de los archivos especificados en los elementos `<file>` y, a continuación, actualizará los atributos hash con el valor calculado.  
  
 **Actualizar ruta de búsqueda de hash de archivo**  
 Especifica la ruta de búsqueda de los archivos a los que se hace referencia en los elementos `<file>`.  Esta opción también utiliza la opción \/hashupdate.  
  
## Vea también  
 [Elemento \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)   
 [Manifiesto de aplicación ClickOnce](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Herramienta Manifiesto \(Páginas de propiedades\)](../ide/manifest-tool-property-pages.md)   
 [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md)   
 [Cómo: Editar hojas de propiedades de proyecto](../misc/how-to-edit-project-property-sheets.md)