---
title: Avanzadas, herramienta manifiesto, propiedades de configuración, &lt;NombreDelProyecto > cuadro de diálogo páginas de propiedades
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
ms.assetid: 3d587366-05ea-4956-a978-313069660735
ms.openlocfilehash: a20e474deb69099c53ad656dda5406e7161a1695
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295144"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Avanzadas, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;Nombre_Proyecto&gt; (Cuadro de diálogo)

Use este cuadro de diálogo para especificar las opciones avanzadas de [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades de configuración** y, después, seleccione **Avanzadas**.

## <a name="uielement-list"></a>Lista de UIElement

- **Actualizar hash de archivo**

   Use la opción /hashupdate para especificar que la herramienta Manifiesto calculará el hash de los archivos especificados en los elementos `<file>` y, después, actualice los atributos de hash de con el valor calculado.

- **Actualizar ruta de búsqueda de hash de archivo**

   Especifica la ruta de acceso de búsqueda para los archivos a los que se hace referencia en los elementos `<file>`. Esta opción también usa la opción /hashupdate.

## <a name="see-also"></a>Vea también

[Elemento \<file>](/visualstudio/deployment/file-element-clickonce-application)<br>
[ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)<br>
[Páginas de propiedades de la herramienta Manifiesto](manifest-tool-property-pages.md)<br>
[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md)
