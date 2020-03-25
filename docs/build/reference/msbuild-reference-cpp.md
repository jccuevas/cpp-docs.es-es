---
title: Referencia de MSBuild C++ para proyectos en Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168907"
---
# <a name="msbuild-reference-for-c-projects"></a>Referencia de MSBuild para proyectos de C++

MSBuild es el sistema de compilación nativo para todos los proyectos de Visual Studio C++ , incluidos los proyectos. Al compilar un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, invoca la herramienta MSBuild. exe, que a su vez usa el archivo de proyecto. vcxproj, y varios archivos. targets y. props. En general, se recomienda encarecidamente usar el IDE de Visual Studio para establecer las propiedades del proyecto e invocar MSBuild. La edición manual de archivos de proyecto puede provocar problemas graves si no se realiza correctamente.

Si, por alguna razón, desea usar MSBuild directamente desde la línea de comandos, vea [usar MSBuild desde la línea de comandos](../msbuild-visual-cpp.md). Para obtener más información sobre MSBuild en general, vea [msbuild](/visualstudio/msbuild/msbuild) en la documentación de Visual Studio.

## <a name="in-this-section"></a>En esta sección

[Parámetros internos de MSBuild para proyectos de C++](msbuild-visual-cpp-overview.md)<br/>
Información sobre cómo se almacenan y consumen propiedades y destinos.

[Macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md)<br/>
Describe las macros (constantes en tiempo de compilación) que se pueden usar para definir propiedades como las rutas de acceso y las versiones del producto.

[Tipos de archivo creados C++ para proyectos](file-types-created-for-visual-cpp-projects.md)<br/>
Describe los distintos tipos de archivos que Visual Studio crea para distintos tipos de proyecto.

[Plantillas de C++ proyecto de Visual Studio](visual-cpp-project-types.md)<br>
Describe los tipos de proyecto basados en MSBuild que están disponibles C++para.

[Nuevas plantillas de elemento C++](using-visual-cpp-add-new-item-templates.md)<br>
Describe los archivos de código fuente y otros elementos que se pueden agregar a un proyecto de Visual Studio.

[Archivos de encabezado precompilados](../creating-precompiled-header-files.md) Cómo usar archivos de encabezado precompilados y cómo crear su propio código precompilado personalizado para acelerar los tiempos de compilación.

[Referencia de propiedades de proyecto de Visual Studio](property-pages-visual-cpp.md)<br/>
Documentación de referencia de las propiedades del proyecto que se establecen en el IDE de Visual Studio.

## <a name="see-also"></a>Consulte también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)
