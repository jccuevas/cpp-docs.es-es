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
ms.openlocfilehash: 916b6615d80000d601c909f771a1ec8f1b947927
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177346"
---
# <a name="resources-property-page"></a>Página de propiedades recursos

En el caso de los programas de escritorio de Windows nativos, la compilación invoca al compilador de [recursos (RC. exe)](/windows/win32/menurc/resource-compiler) para agregar imágenes, tablas de cadenas y archivos *. res* al archivo binario. Las propiedades expuestas en esta página de propiedades se pasan al compilador de C++ recursos, no al compilador o al enlazador. Para obtener más información sobre las propiedades que se enumeran aquí y cómo se asignan a las opciones de línea de comandos de RC, consulte [uso de RC (la línea de comandos de RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Para obtener información sobre cómo obtener acceso a las páginas de propiedades de **recursos** , vea [ C++ establecer las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md). Para acceder a estas propiedades mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Las propiedades de los recursos C++de .net en las aplicaciones/CLI se exponen en la [Página de propiedades recursos administrados](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Especifica una o más definiciones para el compilador de recursos. (/d [macro])

## <a name="undefine-preprocessor-definitions"></a>Anular definiciones del preprocesador

Anula la definición de un símbolo. /u

## <a name="culture"></a>culture

Muestra la referencia cultural (por ejemplo, Inglés de EE. UU. o italiano) utilizada en los recursos. (/l [número])

## <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o más directorios que se van a agregar a la ruta de acceso de inclusión; Use el delimitador de punto y coma si hay más de uno. (/I [rutaDeAcceso])

## <a name="ignore-standard-include-paths"></a>Omitir rutas de acceso de inclusión estándar

Impide que el compilador de recursos busque archivos de inclusión en los directorios especificados en las variables de entorno INCLUDE. /X

## <a name="show-progress"></a>Mostrar progreso

Enviar mensajes de progreso a la ventana de salida. /v

## <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprimir la presentación de la pancarta de inicio y el mensaje de información (/nologo)

## <a name="resource-file-name"></a>Nombre del archivo de recursos

Especifica el nombre del archivo de recursos (/fo [archivo])

## <a name="null-terminate-strings"></a>Cadenas de finalización nulas 

Anexe null a todas las cadenas de las tablas de cadenas. /n

## <a name="see-also"></a>Vea también

[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)