---
title: Manifiesto herramienta propiedades de entrada y salida (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs:
- C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77137e9bc0a4af60080234aac85afa59034d2c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Entrada y salida, herramienta, propiedades de configuración, manifiesto &lt;Projectname&gt; cuadro de diálogo páginas de propiedades
Utilice este cuadro de diálogo para especificar opciones de entrada y salidas para [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para obtener acceso a este cuadro de diálogo de la página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el **herramienta manifiesto** nodo bajo **propiedades de configuración**y, a continuación, seleccione **de entrada y salida**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Archivos de manifiesto adicionales**  
 Usa el **/manifest** opción para especificar las rutas de acceso completas de archivos de manifiesto adicionales que va a procesar la herramienta de manifiesto o de mezcla. Rutas de acceso completas se delimitan mediante un punto y coma.  
  
 **Manifiestos de recursos de entrada**  
 Usa el **/inputresource** opción para especificar la ruta de acceso completa de un recurso de tipo RT_MANIFEST, para introducir en la herramienta de manifiesto. La ruta de acceso puede ir seguido por el identificador de recurso especificado. Por ejemplo:  
  
 `dll_with_manifest.dll;#1`  
  
 El identificador de recurso es opcional y tiene como valor predeterminado CREATEPROCESS_MANIFEST_RESOURCE_ID en winuser.h.  
  
 **Incrustar manifiesto**  
 **Sí** especifica que el sistema de proyectos incrustará el archivo de manifiesto de aplicación en el ensamblado.  
  
 **Ya no** especifica que el sistema del proyecto creará el archivo de manifiesto de aplicación como un archivo independiente.  
  
 **Archivo de manifiesto de salida**  
 Especifica el nombre del archivo de manifiesto de salida. Esta propiedad es opcional cuando sólo un archivo de manifiesto se realizan operaciones con ellos mediante la herramienta de manifiesto.  
  
 **Archivo de recurso del manifiesto**  
 Especifica la salida de los archivos de recursos que se usan para incrustar el manifiesto en la salida del proyecto.  
  
 **Generar archivos de catálogo**  
 Usa el **/makecdfs** opción para especificar que la herramienta de manifiesto generará archivos de definición de catálogo (archivos .cdf), que se utilizan para crear catálogos.  
  
 **Generar manifiesto de ManagedAssembly**  
 Genera un manifiesto de un ensamblado administrado. (**- managedassemblyname:***archivo*).  
  
 **Suprimir elemento de dependencia**  
 Usar con el **- managedassembly** opción. Esta etiqueta suprime la generación de elementos de dependencia en el manifiesto final.  
  
 **Generar etiquetas de categoría**  
 Usar con el **- managedassembly** opción. Esta etiqueta hace que las etiquetas de categoría que se genere.  
  
 **Habilitar el reconocimiento de PPP**  
 Especifica si la aplicación es compatible con PPP. De forma predeterminada, el valor es **Sí** para proyectos MFC y **n** porque solo los proyectos MFC han creado en el reconocimiento de PPP, en caso contrario. Puede invalidar la configuración a **Sí** si agrega código para controlar los diferentes valores de PPP. La aplicación puede aparecer borrosa o pequeña si se establece como reconocimiento de PPP cuando no lo está.  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   