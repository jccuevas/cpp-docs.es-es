---
title: "Página de propiedades General (proyecto) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbe19414dbbe664f15ea2bbbc35a26827ac5b831
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="general-property-page-project"></a>Página de propiedades General (Proyecto)

Cuando haga doble clic en un nodo del proyecto en Explorador de soluciones y seleccione **propiedades**, **General** página de propiedades bajo la **propiedades de configuración** nodo en el panel izquierdo muestra dos secciones de propiedades:

- General

- Valores predeterminados del proyecto

Para los proyectos de distinta de Windows, vea [referencia de página de propiedades de C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="general"></a>General

Las propiedades en la sección General afectan a la ubicación de archivos que se crean en el proceso de compilación y los archivos que se eliminarán cuando el **limpiar** opción (**generar** menú) está seleccionado.

**Plataforma de destino**  
Especifica la plataforma en la que se ejecutará el proyecto. Por ejemplo, Windows, Android o iOS. El valor **Windows 10** significa que el proyecto tiene como destino la plataforma Universal de Windows. Si se están destinadas a versiones anteriores de Windows, no se muestra la versión y el valor de este campo aparece simplemente como **Windows**. Este es un campo de solo lectura que se establece al crear un proyecto.

**Versión del SDK de Windows**  
Para la plataforma de destino de Windows, especifica la versión del SDK de Windows que requiera el proyecto. Cuando se instala una carga de trabajo de C++ mediante el instalador de Visual Studio, también se instalan los componentes necesarios de Windows SDK. Si tiene otras versiones del SDK de Windows en el equipo, todas las versiones de las herramientas SDK que ha instalado se mostrarán en la lista desplegable.

Que tenga como destino Windows 7 o Windows Vista, use el valor **8.1**, ya que Windows SDK 8.1 es compatible con estas plataformas. Además, debe definir el valor adecuado para **_WIN32_WINNT** en targetver.h. Para Windows 7, es 0x0601. Vea [Modificar WINVER y _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Puede instalar el conjunto de herramientas de plataforma de Windows XP incluida en Visual Studio para usar la versión actual de las bibliotecas para compilar proyectos de Windows XP y Windows Server 2003. Para obtener información acerca de cómo obtener y usar este conjunto de herramientas de plataforma, consulte [configurar programas para Windows XP](../build/configuring-programs-for-windows-xp.md). Para más información sobre cómo cambiar el conjunto de herramientas de la plataforma, vea [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Versión mín. de la plataforma de destino**  
Especifica la versión más antigua de la plataforma en la que se puede ejecutar el proyecto. Esta propiedad solo aparece si el tipo de proyecto lo admite, como en el caso de proyectos universales de Windows. Si la aplicación puede aprovechar las características de una versión más reciente del SDK de Windows, pero todavía se puede ejecutar en versiones anteriores sin esas características, quizás el valor de estas dos propiedades podría ser diferente con alguna pérdida de funcionalidad. De ser así, el código debe comprobar la versión de la plataforma en la que se está ejecutando en tiempo de ejecución y no intentar usar características que no están disponibles en una versión anterior de la plataforma.

Tenga en cuenta que Visual C++ no aplica esta opción. Se incluye para proporcionar consistencia con otros lenguajes, como C# y JavaScript, y como una guía para cualquier persona que use su proyecto. Visual C++ no generarán un error si usa una característica que no esté disponible en la versión mínima.

**Directorio de salida**  
Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos de salida que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el vinculador, el bibliotecario o BSCMake. De forma predeterminada, esta propiedad es el directorio especificado por el macros $(SolutionDir) $(Configuration) \.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

**Directorio intermedio**  
Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos intermedios que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el compilador de C/C++, MIDL y el compilador de recursos. De forma predeterminada, esta propiedad es el directorio especificado por la macro $(Configuration) \.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

**Nombre de destino**  
Especifica el nombre de archivo que este proyecto genera. De forma predeterminada, esta propiedad es el nombre de archivo especificado por la macro $(ProjectName).

**Extensión de destino**  
Especifica la extensión de nombre de archivo que este proyecto genera; por ejemplo, .exe o .dll.

**Extensiones para eliminar al limpiar**  
El **limpiar** opción (**generar** menú) elimina archivos del directorio intermedio en el que se compila la configuración de un proyecto. Archivos con las extensiones especificadas con esta propiedad será eliminado al **limpiar** es ejecución o cuando se realiza una recompilación. Además de los archivos del directorio intermedio que tienen estas extensiones, el sistema de compilación también eliminará todos los resultados conocidos de la compilación independientemente de dónde se encuentren (incluidos los resultados intermedios, como los archivos .obj). Tenga en cuenta que puede especificar caracteres comodín.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

**Crear archivo de registro**  
Permite especificar una ubicación no predeterminada para el archivo de registro que se crea cada vez que se compila un proyecto. La ubicación predeterminada es especificada por el .log de macros $(IntDir) $(MSBuildProjectName).

Puede utilizar macros de proyecto para cambiar la ubicación del directorio. Vea [comunes Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).

**Conjunto de herramientas de plataforma**  
Permite al proyecto elegir como destino una versión diferente de las bibliotecas y el compilador de Visual C++. Proyectos de Visual C++ pueden tener como destino cualquier conjunto de herramientas predeterminado instalado Visual Studio, o uno de los conjuntos de herramientas instalado por varias versiones anteriores de Visual Studio, incluidos los conjuntos de herramientas que crean los archivos ejecutables que se pueden ejecutar en Windowx XP. Para obtener información acerca de cómo cambiar el conjunto de herramientas de plataforma, consulte [Cómo: modificar plataforma de destino y el conjunto de herramientas de plataforma](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Habilitar generación Incremental administrado**  
Para los proyectos administrados, esto permite la detección de visibilidad externa al generar los ensamblados. Si un cambio en un proyecto administrado no está visible para otros proyectos, los proyectos dependientes no se recompila. Esto puede mejorar considerablemente los tiempos de compilación de soluciones que incluyen proyectos administrados.

## <a name="project-defaults"></a>Valores predeterminados del proyecto

Las propiedades de la sección Valores predeterminados del proyecto representan propiedades predeterminadas que puede modificar. La definición de estas propiedades se puede encontrar en los archivos .props *directorio de instalación*\VC\VCProjectDefaults.

**Tipo de configuración**  
Se puede elegir entre varios tipos de configuración diferentes:

- **Aplicación (.exe)**, muestra el conjunto de herramientas del vinculador (compilador de C/C ++, MIDL, compilador de recursos, vinculador, BSCMake, XML Web Service Proxy Generator, compilación personalizada, eventos previos, previos, generación).

- **Biblioteca dinámica (.dll)**, muestra el conjunto de herramientas del vinculador, especifica la opción /DLL del vinculador y agrega la definición _WINDLL a CL.

- **Archivo MAKE**, muestra el conjunto de herramientas de archivos MAKE (NMake).

- **Biblioteca estática (.lib)**, muestra el conjunto de herramientas de bibliotecario (igual que el conjunto de herramientas del vinculador diferencia sustituir bibliotecario del vinculador y se omite el generador de Proxy de servicios Web de XML).

- **Utilidad**, muestra el conjunto de herramientas de la utilidad (MIDL, compilación personalizada, eventos, previos y posterior).

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

**Uso de MFC**  
Especifica si el proyecto MFC se vinculará de forma estática o dinámica al archivo DLL de MFC. Pueden seleccionar proyectos MFC no **utilizar bibliotecas estándar de Windows** para vincular con distintas bibliotecas Win32 que se incluyen cuando se utiliza MFC.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

**Uso de ATL**  
Especifica si el proyecto ATL se vinculará de forma estática o dinámica al archivo .DLL de ATL. Si especifica algo distinto de **no utilizar ATL**, definir se agregarán al compilador **línea de comandos** página de propiedades.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.

**Juego de caracteres**  
Define si se debe establecer _UNICODE o _MBCS. También afecta al punto de entrada del vinculador cuando sea necesario.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

**Compatible con Common Language Runtime**  
Hace que la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) que se use la opción del compilador.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

**Versión de destino de .NET Framework**  
En los proyectos administrados, especifica la versión de .NET framework al destino.

**Optimización completa del programa**  
Especifica la [/GL](../build/reference/gl-whole-program-optimization.md) opción del compilador y [/LTCG](../build/reference/ltcg-link-time-code-generation.md) opción del vinculador. De forma predeterminada, esto se deshabilita para configuraciones de depuración y habilita para configuraciones de venta directa.

**Compatibilidad con aplicaciones de la tienda de Windows**  
Especifica si este proyecto admite aplicaciones de la tienda de Windows. Para obtener más información, consulte [/ZW (compilación de Windows en tiempo de ejecución)](../build/reference/zw-windows-runtime-compilation.md)y el centro de desarrolladores de Windows.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../ide/property-pages-visual-cpp.md)  