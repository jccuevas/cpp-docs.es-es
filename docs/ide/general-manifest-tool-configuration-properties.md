---
title: "General, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.MergeRulesFile"
  - "VC.Project.VCManifestTool.UseUnicodeResponseFiles"
  - "VC.Project.VCManifestTool.SuppressStartupBanner"
  - "VC.Project.VCManifestTool.UseFAT32Workaround"
  - "VC.Project.VCManifestTool.VerboseOutput"
  - "VC.Project.VCManifestTool.AssemblyIdentity"
dev_langs: 
  - "C++"
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# General, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este cuadro de diálogo se utiliza para especificar las opciones generales de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para tener acceso a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades correspondientes al proyecto, o bien la hoja de propiedades.  Expanda el nodo de la **Herramienta Manifiesto** bajo **Propiedades de configuración** y, a continuación, seleccione **General**.  
  
## Lista de UIElement  
 **Suprimir la pancarta de inicio**  
 **Sí \(\/nologo\)** especifica que se ocultarán los datos de copyright de Microsoft con carácter estándar cuando se inicie la herramienta de manifiesto.  Use esta opción para suprimir el resultado no deseado en los archivos de registro, cuando ejecute mt.exe como parte de un proceso de compilación o desde un entorno de compilación.  
  
 **Resultado detallado**  
 **Sí \(\/verbose\)** especifica que se mostrará información de compilación adicional durante la generación del manifiesto.  
  
 **Identidad del ensamblado**  
 Utiliza la opción \/identity para especificar una cadena de identidad, que comprende los atributos de [Elemento \<assemblyIdentity\>](../Topic/%3CassemblyIdentity%3E%20Element%20\(ClickOnce%20Application\).md).  Una cadena de identidad comienza con el valor del atributo `name` y va seguida de los pares *atributo* \= *valor*.  Una coma delimita los atributos en una cadena de identidad.  
  
 A continuación se muestra un ejemplo de una cadena de identidad:  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Herramienta Manifiesto \(Páginas de propiedades\)](../ide/manifest-tool-property-pages.md)   
 [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md)   
 [Cómo: Editar hojas de propiedades de proyecto](../misc/how-to-edit-project-property-sheets.md)