---
title: Página de propiedades avanzadas (proyecto)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328426"
---
# <a name="advanced-property-page"></a>Página de propiedades avanzadas

La página de propiedades Avanzadas está disponible en Visual Studio 2019 y versiones posteriores.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Propiedades avanzadas

- **Extensión de archivo de destino**

   Especifica la extensión de archivo que se usará para la salida de compilación. El valor predeterminado **es .exe** para aplicaciones, **.lib** para bibliotecas estáticas y **.dll** para archivos DLL.

- **Extensiones para eliminar al limpiar**

   La opción **Limpiar** (menú **Compilar**) elimina archivos del directorio intermedio en el que se compila la configuración de un proyecto. Los archivos que tengan las extensiones especificadas con esta propiedad se eliminarán al ejecutar **Limpiar** o cuando se recompile. Además de los archivos del directorio intermedio que tienen estas extensiones, el sistema de compilación también eliminará todos los resultados conocidos de la compilación independientemente de dónde se encuentren (incluidos los resultados intermedios, como los archivos .obj). Tenga en cuenta que puede especificar caracteres comodín.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Archivo de registro de compilación**

   Permite especificar una ubicación no predeterminada para el archivo de registro que se crea cada vez que se compila un proyecto. La ubicación predeterminada se especifica mediante las macros $(IntDir)$(MSBuildProjectName).log.

   Puede utilizar macros de proyecto para cambiar la ubicación del directorio. Consulte [Macros comunes para crear comandos y propiedades.](common-macros-for-build-commands-and-properties.md)

- **Arquitectura de herramientas de construcción preferida**

   Especifica si se deben utilizar las herramientas de compilación x86 o x64.

- **Usar bibliotecas de depuración**

   Especifica si se debe crear una compilación DEBUG o RELEASE.

- **Habilitar la compilación de Unity (JUMBO)**

   Habilita un proceso de compilación en el que muchos archivos de origen de C++ se combinan en uno o varios archivos de "unidad" antes de la compilación para mejorar el rendimiento de compilación. No relacionado con el motor de juego de Unity.

- **Uso de MFC**

   Especifica si el proyecto MFC se vinculará de forma estática o dinámica al archivo DLL de MFC. En los proyectos que no son de MFC se puede seleccionar **Utilizar bibliotecas estándar de Windows** para vincular a distintas bibliotecas Win32 que se incluyen cuando se usa MFC.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Juego de caracteres**

   Define si se debe establecer _UNICODE o _MBCS. También afecta al punto de entrada del vinculador cuando sea necesario.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimización de todo el programa**

   Especifica la opción [/GL](gl-whole-program-optimization.md) del compilador y la opción [/LTCG](ltcg-link-time-code-generation.md) del vinculador. De forma predeterminada, esto se deshabilita para las configuraciones de depuración y se habilita para las comerciales.

- **Versión de conjunto de herramientas MSVC**

   Especifica la versión completa del conjunto de herramientas MSVC que se usará para compilar el proyecto. Si tiene varias versiones de actualización y vista previa de un conjunto de herramientas instalados, puede especificar cuál utilizar aquí.

## <a name="ccli-properties"></a>Propiedades de C++/CLI

- **Compatible con Common Language Runtime**

   Hace que se use la opción [/clr](clr-common-language-runtime-compilation.md) del compilador.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Versión de .NET Framework de destino**

   En los proyectos administrados, especifica la versión de .NET Framework de destino.

- **Habilitar compilación incremental administrada**

   Para los proyectos administrados, esto permite la detección de visibilidad externa al generar los ensamblados. Si un cambio en un proyecto administrado no es visible para otros proyectos, los proyectos dependientes no se recompilan. Esto puede mejorar considerablemente los tiempos de compilación de las soluciones que incluyen proyectos administrados.

::: moniker-end
