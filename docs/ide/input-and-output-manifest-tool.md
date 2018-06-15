---
title: Propiedades de entrada y salida de la herramienta Manifiesto (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15be7636188bb670febd7875974d683c1d78360f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331563"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Entrada y salida, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;NombreDeProyecto&gt; (Cuadro de diálogo)
Use este cuadro de diálogo para especificar opciones de entrada y salida para [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades de configuración** y, después, seleccione **Entrada y salida**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Archivos de manifiesto adicionales**  
 Usa la opción **/manifest** para especificar las rutas de acceso completas de los archivos de manifiesto adicionales que la herramienta Manifiesto va a procesar o combinar. Las rutas de acceso completas se delimitan mediante un punto y coma.  
  
 **Manifiestos de recursos de entrada**  
 Usa la opción **/inputresource** para especificar la ruta de acceso completa de un recurso de tipo RT_MANIFEST, para agregar como entrada a la herramienta Manifiesto. La ruta de acceso puede ir seguida por el identificador de recurso especificado. Por ejemplo:  
  
 `dll_with_manifest.dll;#1`  
  
 El identificador de recurso es opcional y tiene como valor predeterminado CREATEPROCESS_MANIFEST_RESOURCE_ID en winuser.h.  
  
 **Incrustar manifiesto**  
 **Sí** especifica que el sistema de proyectos insertará el archivo de manifiesto de aplicación en el ensamblado.  
  
 **No** especifica que el sistema de proyectos creará el archivo de manifiesto de aplicación como un archivo independiente.  
  
 **Archivo de manifiesto de salida**  
 Especifica el nombre del archivo de manifiesto de salida. Esta propiedad es opcional solo cuando la herramienta Manifiesto realiza operaciones en un archivo de manifiesto.  
  
 **Archivo de recursos de manifiesto**  
 Especifica el archivo de recursos de salida que se usa para insertar el manifiesto en la salida del proyecto.  
  
 **Generar archivos de catálogo**  
 Usa la opción **/makecdfs** para especificar que la herramienta Manifiesto generará archivos de definición de catálogo (archivos .cdf), que se usan para crear catálogos.  
  
 **Generar manifiesto a partir de ManagedAssembly**  
 Genera un manifiesto a partir de un ensamblado administrado. (**-nombre_ensamblado_administrado:***archivo*).  
  
 **Suprimir elemento de dependencia**  
 Se usa con la opción **-ensamblado_administrado**. Esta etiqueta suprime la generación de elementos de dependencia en el manifiesto final.  
  
 **Generar etiquetas de categoría**  
 Se usa con la opción **-ensamblado_administrado**. Esta etiqueta hace que se generen etiquetas de categoría.  
  
 **Habilitar reconocimiento de PPP**  
 Especifica si la aplicación es compatible con PPP. De forma predeterminada, el valor es **Sí** para proyectos MFC y **No** en caso contrario, porque solo los proyectos MFC cuentan con reconocimiento de PPP integrado. Puede reemplazar la configuración por **Sí** si agrega código para controlar otros valores de PPP. Es posible que la aplicación se vea borrosa o pequeña si se establece como compatible con PPP cuando no lo es.  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta Manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   