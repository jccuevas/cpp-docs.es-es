---
title: Herramienta manifiesto aislada propiedades COM (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c425a71f8bb8a7972ade29fb0d18cf3eab7debb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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