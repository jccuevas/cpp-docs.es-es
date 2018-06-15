---
title: Avanzadas, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;Nombre_Proyecto&gt; (Cuadro de diálogo) | Microsoft Docs
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
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33326942"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Avanzadas, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;Nombre_Proyecto&gt; (Cuadro de diálogo)
Use este cuadro de diálogo para especificar las opciones avanzadas de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades de configuración** y, después, seleccione **Avanzadas**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Actualizar hash de archivo**  
 Use la opción /hashupdate para especificar que la herramienta Manifiesto calculará el hash de los archivos especificados en los elementos `<file>` y, después, actualice los atributos de hash de con el valor calculado.  
  
 **Actualizar ruta de búsqueda de hash de archivo**  
 Especifica la ruta de acceso de búsqueda para los archivos a los que se hace referencia en los elementos `<file>`. Esta opción también usa la opción /hashupdate.  
  
## <a name="see-also"></a>Vea también  
 [Elemento \<file>](/visualstudio/deployment/file-element-clickonce-application)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta Manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   