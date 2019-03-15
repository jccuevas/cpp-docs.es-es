---
title: Herramienta manifiesto COM aislado propiedades
ms.date: 12/10/2018
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 2fda169ecf304373d27d699bf313bde124dc399f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827495"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM aislado, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;Nombre_Proyecto&gt; (Cuadro de diálogo)

Use este cuadro de diálogo para especificar opciones de **COM aislado** para [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades comunes** y, después, seleccione **COM aislado**.

## <a name="task-list"></a>Lista de tareas

- [Cómo: Compilar aplicaciones aisladas que empleen componentes COM](../how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>Lista de UIElement

- **Archivo de biblioteca de tipos**

   Usa la opción /tlb para especificar el nombre del archivo de biblioteca de tipos (archivo .tlb) que la herramienta Manifiesto va a usar para generar el archivo de manifiesto.

- **Archivo de script de registro**

   Usa la opción /rgs para especificar el nombre del archivo de script de registro (archivo .rgs) que la herramienta Manifiesto va a usar para generar el archivo de manifiesto.

- **Nombre de archivo del componente**

   Usa la opción /dll para especificar el nombre del recurso que la herramienta Manifiesto va a generar. Debe escribir un valor para esta propiedad cuando se especifiquen valores para **Archivo de biblioteca de tipos** o **Archivo de script de registro**.

- **Archivo de reemplazo**

   Usa la opción /replacements para especificar la ruta de acceso completa al archivo que contiene los valores para las cadenas reemplazables en el archivo .rgs.

## <a name="see-also"></a>Vea también

[Aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications)<br>
[ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)<br>
[Páginas de propiedades de la herramienta Manifiesto](manifest-tool-property-pages.md)<br>
[Establece el compilador de C++ y crear propiedades en Visual Studio](../working-with-project-properties.md)
