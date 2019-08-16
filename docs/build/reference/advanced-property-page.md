---
title: Página de propiedades avanzadas (proyecto)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315534"
---
# <a name="advanced-property-page"></a>Página de propiedades avanzadas

La página de propiedades avanzadas está disponible en Visual Studio 2019 y versiones posteriores.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Propiedades avanzadas

- **Extensión de archivo de destino**

   Especifica la extensión de archivo que se va a usar para la salida de la compilación. El valor predeterminado es **. exe** para las aplicaciones, **. lib** para las bibliotecas estáticas y **. dll** para archivos dll.

- **Extensiones para eliminar al limpiar**

   La opción **Limpiar** (menú **Compilar**) elimina archivos del directorio intermedio en el que se compila la configuración de un proyecto. Los archivos que tengan las extensiones especificadas con esta propiedad se eliminarán al ejecutar **Limpiar** o cuando se recompile. Además de los archivos del directorio intermedio que tienen estas extensiones, el sistema de compilación también eliminará todos los resultados conocidos de la compilación independientemente de dónde se encuentren (incluidos los resultados intermedios, como los archivos .obj). Tenga en cuenta que puede especificar caracteres comodín.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Archivo de registro de compilación**

   Permite especificar una ubicación no predeterminada para el archivo de registro que se crea cada vez que se compila un proyecto. La ubicación predeterminada se especifica mediante las macros $(IntDir)$(MSBuildProjectName).log.

   Puede utilizar macros de proyecto para cambiar la ubicación del directorio. Vea [macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md).

- **Arquitectura de la herramienta de compilación preferida**

   Especifica si se van a usar las herramientas de compilación x86 o x64.

- **Usar bibliotecas de depuración**

   Especifica si se va a crear una compilación de depuración o de versión.

- **Habilitar la compilación de Unity (gigante)**

   Habilita un proceso de compilación en C++ el que muchos archivos de código fuente se combinan en uno o varios archivos "Unity" antes de la compilación para mejorar el rendimiento de la compilación. No está relacionado con el motor de juegos de Unity.

- **Uso de MFC**

   Especifica si el proyecto MFC se vinculará de forma estática o dinámica al archivo DLL de MFC. En los proyectos que no son de MFC se puede seleccionar **Utilizar bibliotecas estándar de Windows** para vincular a distintas bibliotecas Win32 que se incluyen cuando se usa MFC.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Juego de caracteres**

   Define si se debe establecer _UNICODE o _MBCS. También afecta al punto de entrada del vinculador cuando sea necesario.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimización de todo el programa**

   Especifica la opción [/GL](gl-whole-program-optimization.md) del compilador y la opción [/LTCG](ltcg-link-time-code-generation.md) del vinculador. De forma predeterminada, esto se deshabilita para las configuraciones de depuración y se habilita para las comerciales.

- **Versión del conjunto de herramientas MSVC**

   Especifica la versión completa del conjunto de herramientas de MSVC que se usará para compilar el proyecto. Si tiene instaladas varias versiones de vista previa y actualización de un conjunto de herramientas, puede especificar cuál desea usar aquí.

## <a name="ccli-properties"></a>C++Propiedades/CLI

- **Compatible con Common Language Runtime**

   Hace que se use la opción [/clr](clr-common-language-runtime-compilation.md) del compilador.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Versión de .NET Framework de destino**

   En los proyectos administrados, especifica la versión de .NET Framework de destino.

- **Habilitar compilación incremental administrada**

   Para los proyectos administrados, esto permite la detección de visibilidad externa al generar los ensamblados. Si un cambio en un proyecto administrado no es visible para otros proyectos, los proyectos dependientes no se recompilan. Esto puede mejorar considerablemente los tiempos de compilación de las soluciones que incluyen proyectos administrados.

::: moniker-end
