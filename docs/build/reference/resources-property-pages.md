---
title: Recursos
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336073"
---
# <a name="resources-property-page"></a>Página de propiedades recursos

Para los programas de escritorio nativos de Windows, la compilación invoca el compilador de recursos [(rc.exe)](/windows/win32/menurc/resource-compiler) para agregar imágenes, tablas de cadenas y archivos *.res* al binario. Las propiedades expuestas en esta página de propiedades se pasan al compilador de recursos, no al compilador de C++ o al vinculador. Para obtener más información sobre las propiedades enumeradas aquí y cómo se asignan a las opciones de línea de comandos de RC, consulte Uso de RC (la línea de [comandos RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Para obtener información sobre cómo obtener acceso a las páginas de propiedades **Resources,** vea [Establecer el compilador C++ y generar propiedades en Visual Studio](../working-with-project-properties.md). Para acceder a estas propiedades mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Las propiedades de los recursos de .NET en las aplicaciones C++/CLI se exponen en la página de propiedades [Recursos administrados](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Especifica una o más definiciones para el compilador de recursos. (/d[macro])

## <a name="undefine-preprocessor-definitions"></a>Anular definiciones del preprocesador

Anular la definición de un símbolo. (/u)

## <a name="culture"></a>culture

Enumera la referencia cultural (como inglés o italiano de EE. UU.) utilizada en los recursos. (/l [numero])

## <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o varios directorios que se agregará a la ruta de acceso de inclusión; utilizar delimitador de punto y coma si hay más de uno. (/I[ruta])

## <a name="ignore-standard-include-paths"></a>Ignorar rutas de inclusión estándar

Impide que el compilador de recursos busque archivos de inclusión en los directorios especificados en las variables de entorno INCLUDE. (/X)

## <a name="show-progress"></a>Mostrar progreso

Enviar mensajes de progreso a la ventana de salida. (/v)

## <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprimir la visualización del banner de inicio y el mensaje de información (/nologo)

## <a name="resource-file-name"></a>Nombre del archivo de recursos

Especifica el nombre del archivo de recursos (/fo[file])

## <a name="null-terminate-strings"></a>Cadenas de terminación nulas

Anexar null a todas las cadenas de las tablas de cadenas. (/n)

## <a name="see-also"></a>Consulte también

[Referencia de página de propiedades del proyecto C++](property-pages-visual-cpp.md)
