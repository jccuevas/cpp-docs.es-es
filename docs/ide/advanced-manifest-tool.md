---
title: Avanzadas, herramienta manifiesto, propiedades de configuración, &lt;Projectname&gt; cuadro de diálogo páginas de propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d4dc3ab325a7346d0e787a15d69d646896827d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Avanzadas, herramienta manifiesto, propiedades de configuración, &lt;Projectname&gt; cuadro de diálogo páginas de propiedades
Utilice este cuadro de diálogo para especificar las opciones avanzadas de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para obtener acceso a este cuadro de diálogo de la página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el **herramienta manifiesto** nodo bajo **propiedades de configuración**y, a continuación, seleccione **avanzadas**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Actualizar los hash de archivo**  
 Utiliza la opción /hashupdate para especificar que la herramienta manifiesto calculará el hash de los archivos especificados en `<file>` elementos y actualice el hash de atributos con el valor calculado.  
  
 **Actualizar la ruta de búsqueda de hash de archivo**  
 Especifica la ruta de acceso de búsqueda para los archivos que se hace referencia en `<file>` elementos. Esta opción también utiliza la opción/hashupdate.  
  
## <a name="see-also"></a>Vea también  
 [\<archivo > elemento](/visualstudio/deployment/file-element-clickonce-application)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   