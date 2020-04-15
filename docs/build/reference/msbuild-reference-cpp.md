---
title: Referencia de MSBuild para proyectos C++ en Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336207"
---
# <a name="msbuild-reference-for-c-projects"></a>Referencia de MSBuild para proyectos de C++

MSBuild es el sistema de compilación nativo para todos los proyectos de Visual Studio, incluidos los proyectos de C++. Al compilar un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, invoca la herramienta msbuild.exe, que a su vez consume el archivo de proyecto .vcxproj y varios archivos .targets y .props. En general, se recomienda encarecidamente usar el IDE de Visual Studio para establecer las propiedades del proyecto e invocar MSBuild. La edición manual de archivos de proyecto puede dar lugar a problemas graves si no se hace correctamente.

Si por alguna razón desea utilizar MSBuild directamente desde la línea de comandos, vea [Usar MSBuild desde la línea](../msbuild-visual-cpp.md)de comandos . Para obtener más información acerca de MSBuild en general, vea [MSBuild](/visualstudio/msbuild/msbuild) en la documentación de Visual Studio.

## <a name="in-this-section"></a>En esta sección

[Parámetros internos de MSBuild para proyectos de C++](msbuild-visual-cpp-overview.md)<br/>
Información sobre cómo se almacenan y consumen las propiedades y los destinos.

[Macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md)<br/>
Describe macros (constantes en tiempo de compilación) que se pueden usar para definir propiedades como rutas de acceso y versiones de productos.

[Tipos de archivos creados para proyectos C++](file-types-created-for-visual-cpp-projects.md)<br/>
Describe los distintos tipos de archivos que Visual Studio crea para diferentes tipos de proyecto.

[Plantillas de proyecto de Visual Studio C++](visual-cpp-project-types.md)<br>
Describe los tipos de proyecto basados en MSBuild que están disponibles para C++.

[Nuevas plantillas de elemento C++](using-visual-cpp-add-new-item-templates.md)<br>
Describe los archivos de origen y otros elementos que puede agregar a un proyecto de Visual Studio.

Archivos de [encabezado precompilados](../creating-precompiled-header-files.md) Cómo usar archivos de encabezado precompilados y cómo crear su propio código precompilado personalizado para acelerar los tiempos de compilación.

[Referencia de la propiedad del proyecto de Visual Studio](property-pages-visual-cpp.md)<br/>
Documentación de referencia para las propiedades del proyecto que se establecen en el IDE de Visual Studio.

## <a name="see-also"></a>Consulte también

[Referencia de construcción C/C++](c-cpp-building-reference.md)
