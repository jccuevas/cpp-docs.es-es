---
title: Propiedades COM aislado de la herramienta Manifiesto (Visual C++) | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330186"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM aislado, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;Nombre_Proyecto&gt; (Cuadro de diálogo)
Use este cuadro de diálogo para especificar opciones de **COM aislado** para [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades comunes** y, después, seleccione **COM aislado**.  
  
## <a name="task-list"></a>Lista de tareas  
  
-   [Procedimiento para compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Archivo de biblioteca de tipos**  
 Usa la opción /tlb para especificar el nombre del archivo de biblioteca de tipos (archivo .tlb) que la herramienta Manifiesto va a usar para generar el archivo de manifiesto.  
  
 **Archivo de script de registro**  
 Usa la opción /rgs para especificar el nombre del archivo de script de registro (archivo .rgs) que la herramienta Manifiesto va a usar para generar el archivo de manifiesto.  
  
 **Nombre de archivo del componente**  
 Usa la opción /dll para especificar el nombre del recurso que la herramienta Manifiesto va a generar. Debe escribir un valor para esta propiedad cuando se especifiquen valores para **Archivo de biblioteca de tipos** o **Archivo de script de registro**.  
  
 **Archivo de reemplazo**  
 Usa la opción /replacements para especificar la ruta de acceso completa al archivo que contiene los valores para las cadenas reemplazables en el archivo .rgs.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta Manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   