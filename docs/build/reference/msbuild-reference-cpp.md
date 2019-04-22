---
title: Referencia de MSBuild para proyectos de C++ en Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024704"
---
# <a name="msbuild-reference-for-c-projects"></a>Referencia de MSBuild para proyectos de C++

MSBuild es el sistema de compilación nativa para todos los proyectos en Visual Studio, incluidos los proyectos de C++. Cuando compila un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, invoca la herramienta msbuild.exe, que a su vez consume el archivo .vcxproj del proyecto y varios archivos .targets y .props. En general, se recomienda encarecidamente usar el IDE de Visual Studio para establecer las propiedades del proyecto e invocar MSBuild. Editar manualmente archivos de proyecto puede provocar problemas graves si no se realiza correctamente.

Si por algún motivo desea utilizar MSBuild directamente desde la línea de comandos, consulte [usar MSBuild desde la línea de comandos](../msbuild-visual-cpp.md). Para obtener más información acerca de MSBuild en general, vea [MSBuild](/visualstudio/msbuild/msbuild) en la documentación de Visual Studio.

## <a name="in-this-section"></a>En esta sección

[Parámetros internos de MSBuild para proyectos de C++](msbuild-visual-cpp-overview.md)<br/>
Información acerca de cómo se almacenan y consumen propiedades y destinos.

[Macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md)<br/>
Describe las macros (constantes de tiempo de compilación) que pueden utilizarse para definir las propiedades como rutas de acceso y las versiones de producto.

[Tipos de archivos creados para proyectos de C++](file-types-created-for-visual-cpp-projects.md)<br/>
Describe los distintos tipos de archivos que crea Visual Studio para diferentes tipos de proyectos.

[Plantillas de proyecto de Visual Studio C++](visual-cpp-project-types.md)<br>
Describe los tipos de proyecto basado en MSBuild que están disponibles para C++.

[Nuevas plantillas de elemento C++](using-visual-cpp-add-new-item-templates.md)<br>
Describe los archivos de origen y otros elementos que puede agregar a un proyecto de Visual Studio.

[Archivos de encabezado precompilado](../creating-precompiled-header-files.md) cómo utilizar archivos de encabezado precompilado y cómo crear uno personalizado precompilado acelerar los tiempos de compilación de código.

[Referencia de propiedad de proyecto de Visual Studio](property-pages-visual-cpp.md)<br/>
Documentación de referencia para las propiedades del proyecto que se establecen en el IDE de Visual Studio.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)