---
title: "Entrada y salida, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.OutputManifestFile"
  - "VC.Project.VCManifestTool.InputResourceManifests"
  - "VC.Project.VCManifestTool.EmbedManifest"
  - "VC.Project.VCManifestTool.AdditionalManifestFiles"
  - "VC.Project.VCManifestTool.DependencyInformationFile"
  - "VC.Project.VCManifestTool.OutputResourceManifest"
  - "VC.Project.VCManifestTool.GenerateCatalogFiles"
dev_langs: 
  - "C++"
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Entrada y salida, Herramienta Manifiesto, Propiedades de configuraci&#243;n, P&#225;ginas de propiedades de &lt;Projectname&gt; (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este cuadro de diálogo se usa para especificar las opciones de entrada y salida de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para tener acceso a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades correspondientes al proyecto, o bien la hoja de propiedades.  Expanda el nodo de la **Herramienta Manifiesto** bajo **Propiedades de configuración** y, a continuación, seleccione **Entrada y salida**.  
  
## Lista de UIElement  
 **Archivos de manifiesto adicionales**  
 Utiliza la opción **\/manifest** para especificar las rutas de acceso completas de archivos de manifiesto adicionales que procesa o combina la herramienta de manifiesto.  Un punto y coma delimita las rutas de acceso completas.  
  
 **Manifiestos de recursos de entrada**  
 Utiliza la opción **\/inputresource** para especificar la ruta de acceso completa de un recurso del tipo RT\_MANIFEST, para insertarlo en la herramienta de manifiesto.  El identificador de recursos especificado puede seguir la ruta de acceso.  Por ejemplo:  
  
 `dll_with_manifest.dll;#1`  
  
 El identificador de recursos es opcional y tiene como valor predeterminado CREATEPROCESS\_MANIFEST\_RESOURCE\_ID en winuser.h.  
  
 **Incrustar manifiesto**  
 **Sí** especifica que el sistema de proyectos incrustará el archivo de manifiesto de aplicación en el ensamblado.  
  
 **No** especifica que el sistema de proyectos creará el archivo de manifiesto de aplicación como un archivo independiente.  
  
 **Archivo de manifiesto de salida**  
 Especifica el nombre del archivo de manifiesto de salida.  Esta propiedad es opcional cuando la herramienta de manifiesto sólo trabaja con un archivo de manifiesto.  
  
 **Archivo de recursos de manifiesto**  
 Especifica los archivos de recursos de salida utilizados para incrustar el manifiesto en el resultado del proyecto.  
  
 **Generar archivos de catálogo**  
 Utiliza la opción **\/makecdfs** para especificar que la herramienta de manifiesto generará archivos de definición de catálogo \(archivos .cdf\), que se utilizan para crear catálogos.  
  
 **Generar manifiesto de ManagedAssembly**  
 Genera un manifiesto de un ensamblado administrado.  \(**\-managedassemblyname:***archivo*\).  
  
 **Suprimir elemento de dependencia**  
 Se utiliza con la opción **\-managedassembly**.  Esta etiqueta suprime la generación de elementos de dependencia en el manifiesto final.  
  
 **Generar etiquetas de categoría**  
 Se utiliza con la opción **\-managedassembly**.  Esta etiqueta hace que se generen las etiquetas de categoría.  
  
 **Habilitar conocimiento de PPP**  
 Especifica si la aplicación tiene en cuenta los PPP.  De manera predeterminada, el valor es **Yes** para los proyectos MFC y **No** en caso contrario, porque solo los proyectos MFC tienen integrado el reconocimiento de PPP.  Puede invalidar el valor en **Yes** si agrega código para administrar valores PPP diferentes.  Su aplicación puede que aparezca borrosa o pequeña si la establece como que tiene en cuenta el valor de PPP cuando no lo tiene.  
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Herramienta Manifiesto \(Páginas de propiedades\)](../ide/manifest-tool-property-pages.md)   
 [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md)   
 [Cómo: Editar hojas de propiedades de proyecto](../misc/how-to-edit-project-property-sheets.md)