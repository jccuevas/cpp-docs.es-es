---
title: Páginas de propiedades de la herramienta Manifiesto
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: 20ca118b3aacb02333d49b67d13de30f11dc5d8d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079497"
---
# <a name="manifest-tool-property-pages"></a>Páginas de propiedades de la herramienta Manifiesto

Use estas páginas para especificar las opciones generales de [MT. exe](/windows/win32/sbscs/mt-exe). Estas páginas se encuentran en **Project** > **propiedades** > **propiedades de configuración** > **manifest Tool**.

## <a name="general-property-page"></a>Página de propiedades general

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

   **Sí (/nologo)** especifica que los datos de copyright de Microsoft estándar se ocultan cuando se inicia la herramienta Manifiesto. Use esta opción para suprimir la salida no deseada en los archivos de registro, cuando ejecute mt.exe como parte de un proceso de compilación o desde un entorno de compilación.

### <a name="verbose-output"></a>Resultados detallados

   **Sí (/verbose)** especifica que se mostrará información adicional de compilación durante la generación del manifiesto.

### <a name="assembly-identity"></a>Identidad del ensamblado * *

Usa la opción /identity para especificar una cadena de identidad, que incluye los atributos para el [Elemento \<assemblyIdentity>](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Una cadena de identidad comienza con el valor para el atributo `name`, seguido por pares *atributo* = *valor*. Los atributos de una cadena de identidad se delimitan mediante una coma.

Esta es una cadena de identidad de ejemplo: `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Página de propiedades entrada y salida

###  <a name="additional-manifest-files"></a>Archivos de manifiesto adicionales

Usa la opción **/manifest** para especificar las rutas de acceso completas de los archivos de manifiesto adicionales que la herramienta Manifiesto va a procesar o combinar. Las rutas de acceso completas se delimitan mediante un punto y coma. (-manifest [manifest1] [manifest2]...)

###  <a name="input-resource-manifests"></a>Manifiestos de recursos de entrada

Usa la opción **/inputresource** para especificar la ruta de acceso completa de un recurso de tipo RT_MANIFEST, para agregar como entrada a la herramienta Manifiesto. La ruta de acceso puede ir seguida por el identificador de recurso especificado. Por ejemplo:

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>Incrustar manifiesto

- **Sí** especifica que el sistema de proyectos insertará el archivo de manifiesto de aplicación en el ensamblado.

- **No** especifica que el sistema de proyectos creará el archivo de manifiesto de aplicación como un archivo independiente.

###  <a name="output-manifest-file"></a>Archivo de manifiesto de salida

Especifica el nombre del archivo de manifiesto de salida. Esta propiedad es opcional solo cuando la herramienta Manifiesto realiza operaciones en un archivo de manifiesto. (-out: [archivo]; # [ID. de recurso])

###  <a name="manifest-resource-file"></a>Archivo de recursos del manifiesto

Especifica el archivo de recursos de resultados usado para incrustar el manifiesto en los resultados del proyecto.

###  <a name="generate-catalog-files"></a>Generar archivos de catálogo

Usa la opción **/makecdfs** para especificar que la herramienta Manifiesto generará archivos de definición de catálogo (archivos .cdf), que se usan para crear catálogos. /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>Generar manifiesto desde ManagedAssembly

Genera un manifiesto a partir de un ensamblado administrado. (-managedassemblyname: [archivo])

###  <a name="suppress-dependency-element"></a>Suprimir elemento de dependencia

Se usa con-managedassembly. suprime la generación de elementos de dependencia en el manifiesto final. (-nodependency)

###  <a name="generate-category-tags"></a>Generar etiquetas de categoría

Se usa con-managedassembly. -la categoría hace que se generen las etiquetas de categoría. (-categoría)

###  <a name="dpi-awareness"></a>Reconocimiento de PPP

Especifica si la aplicación es compatible con PPP. De forma predeterminada, el valor es **Sí** para proyectos MFC y **No** en caso contrario, porque solo los proyectos MFC cuentan con reconocimiento de PPP integrado. Puede reemplazar la configuración por **Sí** si agrega código para controlar otros valores de PPP. Es posible que la aplicación se vea borrosa o pequeña si se establece como compatible con PPP cuando no lo es.

**Opciones**

- **None**
- **Reconocimiento de PPP alto**
- **Reconocimiento de PPP elevado por monitor**

## <a name="isolated-com-property-page"></a>Página de propiedades COM aislada

Para obtener más información acerca de COM aislado, vea [aplicaciones aisladas](/windows/win32/SbsCs/isolated-applications) y [Cómo: compilar aplicaciones aisladas para consumir componentes com](../how-to-build-isolated-applications-to-consume-com-components.md).

###  <a name="type-library-file"></a>Archivo de biblioteca de tipos

Especifica la biblioteca de tipos que se va a usar para la compatibilidad con el manifiesto COM regfree. (-TLB: [archivo])

###  <a name="registrar-script-file"></a>Archivo de script de registro

Especifica el archivo de script de registro que se va a usar para la compatibilidad con el manifiesto COM regfree. (-RGS: [archivo])

###  <a name="component-file-name"></a>Nombre de archivo de componente

Especifica el nombre de archivo del componente que se compila a partir de los archivos. tlb o. RGS especificados. (-dll: [archivo])

###  <a name="replacements-file"></a>Archivo de reemplazos

Especifica el archivo que contiene los valores para las cadenas reemplazables en el archivo RGS. (reemplazos: [archivo])

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

###  <a name="update-file-hashes"></a>Actualizar los hash de archivo

Calcula el hash de los archivos especificados en los elementos de archivo y actualiza el atributo hash con este valor. (hashupdate: [rutaDeAcceso])

###  <a name="update-file-hashes-search-path"></a>Actualizar ruta de búsqueda de hash de archivo

Especifica la ruta de acceso de búsqueda que se debe usar al actualizar los hash de archivo.

###  <a name="additional-options"></a>Opciones adicionales

Opciones adicionales

## <a name="see-also"></a>Consulte también

[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)
