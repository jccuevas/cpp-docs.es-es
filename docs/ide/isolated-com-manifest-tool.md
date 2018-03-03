---
title: Herramienta manifiesto aislada propiedades COM (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe2098c4caead6ebc9ad4747354ae96f093f2c91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Aislamiento de COM, herramienta manifiesto, propiedades de configuración, &lt;Projectname&gt; cuadro de diálogo páginas de propiedades
Utilice este cuadro de diálogo para especificar **COM aislado** opciones para [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para obtener acceso a este cuadro de diálogo de la página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el **herramienta manifiesto** nodo bajo **propiedades comunes**y, a continuación, seleccione **COM aislado**.  
  
## <a name="task-list"></a>Lista de tareas  
  
-   [Procedimiento para compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Archivo de biblioteca de tipos**  
 Utiliza la opción/tlb para especificar el nombre del archivo de biblioteca de tipo (archivo .tlb) que la herramienta Manifiesto utilizará para generar el archivo de manifiesto.  
  
 **Archivo de Script de registro**  
 Utiliza la opción /rgs para especificar el nombre del archivo de script de registrador (archivo .rgs) que la herramienta Manifiesto utilizará para generar el archivo de manifiesto.  
  
 **Nombre de archivo del componente**  
 Utiliza la opción /dll para especificar el nombre del recurso que generará la herramienta de manifiesto. Debe especificar un valor para esta propiedad cuando los valores para cada uno **archivo de biblioteca de tipos** o **archivo de Script de registrador** se especifican.  
  
 **Archivo de reemplazo**  
 Utiliza la opción /replacements para especificar la ruta de acceso completa al archivo que contiene los valores de las cadenas reemplazables en el archivo .rgs.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   