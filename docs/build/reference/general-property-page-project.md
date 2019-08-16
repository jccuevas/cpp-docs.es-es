---
title: Página de propiedades General (Proyecto)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: 0fb6e1289b44940cabaee02e62690c94ec5bf131
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299770"
---
# <a name="general-property-page-project"></a>Página de propiedades General (Proyecto)

::: moniker range=">=vs-2019"

Este tema se aplica a los proyectos de Visual Studio para Windows. Para los proyectos de Linux, consulte referencia de la [Página de propiedades de Linux C++ ](../../linux/prop-pages-linux.md). Para los proyectos de CMake, consulte [proyectos de CMake en Visual Studio](../cmake-projects-in-visual-studio.md).

Al hacer clic con el botón secundario en un nodo de proyecto en Explorador de soluciones y seleccionar **propiedades**, la página de propiedades **General** en el nodo **propiedades de configuración** del panel izquierdo muestra estas propiedades:

- **Directorio de salida**

   Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos de salida que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el vinculador, el bibliotecario o BSCMake. De forma predeterminada, esta propiedad es el directorio especificado por las macros $(SolutionDir)$(Configuration)\.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Directorio intermedio**

   Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos intermedios que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el compilador de C/C++, MIDL y el compilador de recursos. De forma predeterminada, esta propiedad es el directorio especificado por la macro $(Configuration)\.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Nombre de destino**

   Especifica el nombre de archivo que este proyecto genera. De forma predeterminada, esta propiedad es el nombre de archivo especificado por la macro $(ProjectName).

- **Tipo de configuración**

  Se puede elegir entre varios tipos de configuración diferentes:

  - **Aplicación (.exe)**

     Muestra el conjunto de herramientas del vinculador (Compilador de C/C++, MIDL, Compilador de recursos, Vinculador, BSCMake, Generador del proxy de Servicios web XML; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación).

  - **Biblioteca dinámica (.dll)**

     Muestra el conjunto de herramientas del vinculador, especifica la opción /DLL del vinculador y agrega la definición _WINDLL a CL.

  - **Archivo Make**

     Muestra el conjunto de herramientas para los archivos Make (NMake).

  - **Biblioteca estática (.lib)**

     Muestra el conjunto de herramientas de bibliotecario (igual que el conjunto de herramientas del vinculador, con la diferencia de que incluye un bibliotecario en lugar de un vinculador y se omite el Generador del proxy de servicios web XML).

  - **Utilidad**

     Muestra el conjunto de herramientas de utilidades (MIDL; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación).

  Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Versión de Windows SDK**

   Para la plataforma de destino Windows, especifica la versión de Windows SDK que requiere el proyecto. Cuando se instala una carga de trabajo de C++ mediante el instalador de Visual Studio, también se instalan los componentes necesarios de Windows SDK. Si tiene otras versiones de Windows SDK en el equipo, en la lista desplegable se mostrarán todas las versiones de las herramientas del SDK que haya instalado.

   Para establecer Windows 7 o Windows Vista como destino, use el valor **8.1**, ya que Windows SDK 8.1 es compatible con estas plataformas. Además, debe definir el valor adecuado para **_WIN32_WINNT** en targetver.h. Para Windows 7, es 0x0601. Vea [Modificar WINVER y _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Puede instalar el conjunto de herramientas de la plataforma Windows XP incluido en Visual Studio para usar la versión actual de las bibliotecas para compilar proyectos de Windows XP y Windows 2003. Para obtener más información sobre cómo conseguir y usar este conjunto de herramientas de la plataforma, vea [Configurar programas para Windows XP](../configuring-programs-for-windows-xp.md). Para obtener información adicional sobre cómo cambiar el conjunto de herramientas de la plataforma, consulte el artículo relativo al [procedimiento para modificar la plataforma de destino y el conjunto de herramientas de la plataforma](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Conjunto de herramientas de la plataforma**

   Permite al proyecto elegir como destino una versión diferente de las bibliotecas y el compilador de Visual C++. Los proyectos C++ de Visual Studio pueden tener como destino el conjunto de herramientas predeterminado instalado por Visual Studio, o uno de los conjuntos de herramientas instalados por varias versiones anteriores de Visual Studio, incluidos los conjuntos de herramientas que crean ejecutables que se pueden ejecutar en Windows XP. Para obtener información sobre cómo cambiar el conjunto de [herramientas de la plataforma, consulte Cómo: para modificar la plataforma de destino y el conjunto de herramientas de la plataforma](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **C++Estándar de lenguaje**

   Especifica el estándar de lenguaje que se va a usar. El valor predeterminado es/STD: c++ 14. Especifique/STD: c++ 17 para usar las características de C++ 17 o/STD: c++ + latest para usar C++ 20 u otras características experimentales. Para obtener más información, vea [/STD (especificar la versión estándar del lenguaje)](std-specify-language-standard-version.md) .

::: moniker-end

::: moniker range="<=vs-2017"

En Visual Studio 2015 y Visual Studio 2017, al hacer clic con el botón secundario en un nodo de proyecto en **Explorador de soluciones**y seleccionar **propiedades**, la página de propiedades **General** en el nodo **propiedades de configuración** del panel izquierdo muestra dos secciones de propiedades:

- General

- Valores predeterminados del proyecto

## <a name="general"></a>General

- **Plataforma de destino**

   Especifica la plataforma en la que se ejecutará el proyecto. Por ejemplo, Windows, Android o iOS. El valor **Windows 10** significa que el proyecto tiene como destino la Plataforma universal de Windows. Si se seleccionan versiones anteriores de Windows como destino, no se muestra la versión y el valor de este campo aparece simplemente como **Windows**. Este es un campo de solo lectura que se establece al crear un proyecto.

- **Versión de la plataforma de destino (Visual Studio 2015)**

   Especifica la versión más antigua de la plataforma en la que se puede ejecutar el proyecto. Esta propiedad solo aparece si el tipo de proyecto lo admite. Si la aplicación puede aprovechar las características de una versión más reciente del SDK de Windows, pero todavía se puede ejecutar en versiones anteriores sin esas características, quizás el valor de estas dos propiedades podría ser diferente con alguna pérdida de funcionalidad. De ser así, el código debe comprobar la versión de la plataforma en la que se está ejecutando en tiempo de ejecución y no intentar usar características que no están disponibles en una versión anterior de la plataforma.

   El C++ sistema del proyecto no exige esta opción. Se incluye para proporcionar consistencia con otros lenguajes, como C# y JavaScript, y como una guía para cualquier persona que use su proyecto. Visual C++ no generarán un error si usa una característica que no esté disponible en la versión mínima.

- **Versión de Windows SDK (Visual Studio 2017)**

   Para la plataforma de destino Windows, especifica la versión de Windows SDK que requiere el proyecto. Cuando se instala una carga de trabajo de C++ mediante el instalador de Visual Studio, también se instalan los componentes necesarios de Windows SDK. Si tiene otras versiones de Windows SDK en el equipo, en la lista desplegable se mostrarán todas las versiones de las herramientas del SDK que haya instalado.

   Para establecer Windows 7 o Windows Vista como destino, use el valor **8.1**, ya que Windows SDK 8.1 es compatible con estas plataformas. Además, debe definir el valor adecuado para **_WIN32_WINNT** en targetver.h. Para Windows 7, es 0x0601. Vea [Modificar WINVER y _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Puede instalar el conjunto de herramientas de la plataforma Windows XP incluido en Visual Studio para usar la versión actual de las bibliotecas para compilar proyectos de Windows XP y Windows 2003. Para obtener más información sobre cómo conseguir y usar este conjunto de herramientas de la plataforma, vea [Configurar programas para Windows XP](../configuring-programs-for-windows-xp.md). Para obtener información adicional sobre cómo cambiar el conjunto de herramientas de la plataforma, consulte el artículo relativo al [procedimiento para modificar la plataforma de destino y el conjunto de herramientas de la plataforma](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Directorio de salida**

   Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos de salida que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el vinculador, el bibliotecario o BSCMake. De forma predeterminada, esta propiedad es el directorio especificado por las macros $(SolutionDir)$(Configuration)\.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Directorio intermedio**

   Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos intermedios que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el compilador de C/C++, MIDL y el compilador de recursos. De forma predeterminada, esta propiedad es el directorio especificado por la macro $(Configuration)\.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Nombre de destino**

   Especifica el nombre de archivo que este proyecto genera. De forma predeterminada, esta propiedad es el nombre de archivo especificado por la macro $(ProjectName).

- **Extensión de destino**

   Especifica la extensión de nombre de archivo que este proyecto genera; por ejemplo, .exe o .dll.

- **Extensiones para eliminar al limpiar**

   La opción **Limpiar** (menú **Compilar**) elimina archivos del directorio intermedio en el que se compila la configuración de un proyecto. Los archivos que tengan las extensiones especificadas con esta propiedad se eliminarán al ejecutar **Limpiar** o cuando se recompile. Además de los archivos del directorio intermedio que tienen estas extensiones, el sistema de compilación también eliminará todos los resultados conocidos de la compilación independientemente de dónde se encuentren (incluidos los resultados intermedios, como los archivos .obj). Tenga en cuenta que puede especificar caracteres comodín.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Archivo de registro de compilación**

   Permite especificar una ubicación no predeterminada para el archivo de registro que se crea cada vez que se compila un proyecto. La ubicación predeterminada se especifica mediante las macros $(IntDir)$(MSBuildProjectName).log.

   Puede utilizar macros de proyecto para cambiar la ubicación del directorio. Vea [macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md).

- **Conjunto de herramientas de la plataforma**

   Permite al proyecto elegir como destino una versión diferente de las bibliotecas y el compilador de Visual C++. Los proyectos C++ de Visual Studio pueden tener como destino el conjunto de herramientas predeterminado instalado por Visual Studio, o uno de los conjuntos de herramientas instalados por varias versiones anteriores de Visual Studio, incluidos los conjuntos de herramientas que crean ejecutables que se pueden ejecutar en Windows XP. Para obtener información sobre cómo cambiar el conjunto de [herramientas de la plataforma, consulte Cómo: para modificar la plataforma de destino y el conjunto de herramientas de la plataforma](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Habilitar compilación incremental administrada**

   Para los proyectos administrados, esto permite la detección de visibilidad externa al generar los ensamblados. Si un cambio en un proyecto administrado no es visible para otros proyectos, los proyectos dependientes no se recompilan. Esto puede mejorar considerablemente los tiempos de compilación de las soluciones que incluyen proyectos administrados.

## <a name="project-defaults"></a>Valores predeterminados del proyecto
 
Las propiedades de la sección Valores predeterminados del proyecto representan propiedades predeterminadas que puede modificar. La definición de estas propiedades se puede encontrar en los archivos .props del *Directorio de instalación*\VC\VCProjectDefaults.

- **Tipo de configuración**

  Se puede elegir entre varios tipos de configuración diferentes:

  - **Aplicación (.exe)**

     Muestra el conjunto de herramientas del vinculador (Compilador de C/C++, MIDL, Compilador de recursos, Vinculador, BSCMake, Generador del proxy de Servicios web XML; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación).

  - **Biblioteca dinámica (.dll)**

     Muestra el conjunto de herramientas del vinculador, especifica la opción /DLL del vinculador y agrega la definición _WINDLL a CL.

  - **Archivo Make**

     Muestra el conjunto de herramientas para los archivos Make (NMake).

  - **Biblioteca estática (.lib)**

     Muestra el conjunto de herramientas de bibliotecario (igual que el conjunto de herramientas del vinculador, con la diferencia de que incluye un bibliotecario en lugar de un vinculador y se omite el Generador del proxy de servicios web XML).

  - **Utilidad**

     Muestra el conjunto de herramientas de utilidades (MIDL; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación).

  Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Uso de MFC**

   Especifica si el proyecto MFC se vinculará de forma estática o dinámica al archivo DLL de MFC. En los proyectos que no son de MFC se puede seleccionar **Utilizar bibliotecas estándar de Windows** para vincular a distintas bibliotecas Win32 que se incluyen cuando se usa MFC.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Juego de caracteres**

   Define si se debe establecer _UNICODE o _MBCS. También afecta al punto de entrada del vinculador cuando sea necesario.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Compatible con Common Language Runtime**

   Hace que se use la opción [/clr](clr-common-language-runtime-compilation.md) del compilador.

   Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Versión de .NET Framework de destino**

   En los proyectos administrados, especifica la versión de .NET Framework de destino.

- **Optimización de todo el programa**

   Especifica la opción [/GL](gl-whole-program-optimization.md) del compilador y la opción [/LTCG](ltcg-link-time-code-generation.md) del vinculador. De forma predeterminada, esto se deshabilita para las configuraciones de depuración y se habilita para las comerciales.

- **Compatibilidad con aplicaciones de Microsoft Store**

   Especifica si este proyecto admite aplicaciones de Windows Runtime (Plataforma universal de Windows). Para obtener más información, vea [/ZW (Compilación de Windows Runtime)](zw-windows-runtime-compilation.md), y el Centro para desarrolladores de Windows.

::: moniker-end

## <a name="see-also"></a>Vea también

[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)