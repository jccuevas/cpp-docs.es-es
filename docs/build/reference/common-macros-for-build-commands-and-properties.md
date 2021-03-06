---
title: Macros comunes para comandos y propiedades de MSBuild
ms.date: 08/02/2019
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 5038416a8df3282b426d3298c73520f78e962766
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440170"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Macros comunes para comandos y propiedades de MSBuild

En función de las opciones de instalación, Visual Studio puede poner a su disposición cientos de macros en un proyecto de Visual Studio (basado en MSBuild). Corresponden a las propiedades de MSBuild que se establecen de forma predeterminada o en archivos. props o. targets o en la configuración del proyecto. Estas macros pueden usarse en cualquier parte del cuadro de diálogo **Páginas de propiedades** de un proyecto donde se aceptan cadenas. Estas macros no distinguen mayúsculas de minúsculas.

## <a name="view-the-current-properties-and-macros"></a>Ver las propiedades y macros actuales

Para mostrar todas las macros disponibles actualmente, en el cuadro de diálogo **páginas de propiedades** , en **directorios de VC + +** , elija la flecha desplegable al final de una fila de propiedad. Haga clic en **Editar** y, a continuación, en el cuadro de diálogo Editar, elija el botón **macros** . El conjunto actual de propiedades y macros visibles para Visual Studio se muestra junto con el valor actual para cada una. Para obtener más información, vea la sección **especificar valores definidos por el usuario** de referencia de la [ C++ página de propiedades del proyecto](property-pages-visual-cpp.md).

![Botón macros de VC + +](../media/vcppdir_libdir_macros.png "Menú macros")

## <a name="list-of-common-macros"></a>Lista de macros comunes

En esta tabla se describe un subconjunto utilizado comúnmente de las macros disponibles; Hay muchas más que no aparecen aquí. Vaya al cuadro de diálogo **macros** para ver todas las propiedades y sus valores actuales en el proyecto. Para obtener detalles sobre cómo se crean y usan las definiciones de propiedades de MSBuild como macros en los archivos .props, .targets y .vcxproj, vea [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Descripción|
|-----------|-----------------|
|**$(Configuration)**|El nombre de la configuración del proyecto actual (por ejemplo, "Depuración").|
|**$(DevEnvDir)**|El directorio de instalación de Visual Studio (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\".|
|**$(FrameworkDir)**|El directorio en el que se instaló .NET Framework.|
|**$(FrameworkSDKDir)**|El directorio en el que instaló .NET Framework. .NET Framework pudo haberse instalado como parte de Visual Studio o por separado.|
|**$(FrameworkVersion)**|La versión de .NET Framework usada por Visual Studio. Junto con **$(FrameworkDir)** , la ruta de acceso completa a la versión de .NET Framework que usa Visual Studio.|
|**$(FxCopDir)**|La ruta de acceso al archivo fxcop.cmd. El archivo FxCop. cmd no se instala con todas las ediciones de Visual Studio.|
|**$(IntDir)**|Ruta de acceso al directorio especificado para los archivos intermedios. Si se trata de una ruta de acceso relativa, los archivos intermedios van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad del **directorio intermedio** . No use **$ (outdir)** para definir esta propiedad.|
|**$(OutDir)**|Ruta de acceso al directorio del archivo de salida. Si se trata de una ruta de acceso relativa, los archivos de salida van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Directorio de salida** . No use **$ (IntDir)** para definir esta propiedad.|
|**$(Platform)**|El nombre de la plataforma del proyecto actual, por ejemplo, "Win32".|
|**$ (Nombrecortodeplataforma)**|Nombre corto de la arquitectura actual, por ejemplo, "x86" o "x64".|
|**$(ProjectDir)**|El directorio del proyecto (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\".|
|**$(ProjectExt)**|La extensión de archivo del proyecto. Incluye el "." antes de la extensión de archivo.|
|**$(ProjectFileName)**|El nombre de archivo del proyecto (definido como nombre base + extensión de archivo).|
|**$(ProjectName)**|El nombre base del proyecto.|
|**$(ProjectPath)**|El nombre de ruta de acceso absoluta del proyecto (definido como unidad + ruta de acceso + nombre base + extensión de archivo).|
|**$ (PublishDir)**|La ubicación de salida para el destino de publicación; incluye la barra diagonal inversa final '\\'. Tiene como valor predeterminado la carpeta **$ (outdir) app. publish\\** .|
|**$(RemoteMachine)**|Establece en el valor de la propiedad **Remote Machine** en la página de propiedades de depuración. Para obtener más información, vea [Cambiar la configuración del proyecto para una configuración de depuración de C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$(RootNameSpace)**|El espacio de nombres, si hubiera, que contiene la aplicación.|
|**$(SolutionDir)**|El directorio de la solución (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\". Solo se define cuando se compila una solución en el IDE.|
|**$(SolutionExt)**|La extensión de archivo de la solución. Incluye el "." antes de la extensión de archivo. Solo se define cuando se compila una solución en el IDE.|
|**$(SolutionFileName)**|El nombre de archivo de la solución (definido como nombre base + extensión de archivo). Solo se define cuando se compila una solución en el IDE.|
|**$(SolutionName)**|El nombre base de la solución. Solo se define cuando se compila una solución en el IDE.|
|**$(SolutionPath)**|El nombre de ruta de acceso absoluta de la solución (definido como unidad + ruta de acceso + nombre base + extensión de archivo). Solo se define cuando se compila una solución en el IDE.|
|**$(TargetDir)**|El directorio del archivo de salida principal de la compilación (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\".|
|**$(TargetExt)**|La extensión de archivo del archivo de salida principal de la compilación. Incluye el "." antes de la extensión de archivo.|
|**$(TargetFileName)**|El nombre de archivo del archivo de salida principal de la generación (definido como nombre base + extensión de archivo).|
|**$(TargetName)**|El nombre base del archivo de salida principal de la compilación.|
|**$(TargetPath)**|El nombre de ruta de acceso absoluta del archivo de salida principal de la compilación (definido como unidad + ruta de acceso + nombre base + extensión de archivo).|
|**$(VCInstallDir)**|El directorio en el que se incluye el contenido de C++ de la instalación de Visual Studio. Esta propiedad contiene la versión del conjunto de herramientas C++ de Microsoft (MSVC) de destino, que podría ser diferente del host de Visual Studio. Por ejemplo, al compilar con `$(PlatformToolset) = v140`, **$ (VCInstallDir)** contiene la ruta de acceso a la instalación de Visual Studio 2015.|
|**$(VSInstallDir)**|El directorio en el que instaló Visual Studio. Esta propiedad contiene la versión del conjunto de herramientas de Visual Studio de destino, que podría ser diferente a la del host de Visual Studio. Por ejemplo, al compilar con `$(PlatformToolset) = v110`, **$(VSInstallDir)** contiene la ruta de acceso a la instalación de Visual Studio 2012.|
|**$(WebDeployPath)**|La ruta de acceso relativa desde la raíz de la implementación web donde residen las salidas del proyecto.|
|**$(WebDeployRoot)**|La ruta de acceso absoluta a la ubicación de **\<localhost>** . Por ejemplo, c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Macros obsoletas

El sistema de compilación de C++ se ha cambiado significativamente entre Visual Studio 2008 y Visual Studio 2010. Muchas macros que se usaban en los tipos de proyectos anteriores se han cambiado por otras nuevas. Estas macros ya no se usan o se han reemplazado por una o varias propiedades equivalentes o valores de [macro de metadatos de elemento](/visualstudio/msbuild/itemmetadata-element-msbuild) ( **%(** _nombre_ **)** ). Las macros que se marcan como "migradas" se pueden actualizar mediante la herramienta de migración de proyectos. Si el proyecto que contiene la macro se migra desde Visual Studio 2008 o una versión anterior a Visual Studio 2010, Visual Studio convierte la macro a la macro equivalente actual. En las versiones posteriores de Visual Studio no se pueden convertir proyectos de Visual Studio 2008 y versiones anteriores al nuevo tipo de proyecto. Debe convertir estos proyectos en dos pasos: en primer lugar convertirlos a Visual Studio 2010 y, después, convertir el resultado a la versión más reciente de Visual Studio. Para obtener más información, vea [Información general sobre posibles problemas de actualización](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Descripción|
|-----------|-----------------|
|**$(InputDir)**|(Migrado). Directorio del archivo de entrada (definido como unidad + ruta de acceso); incluye la barra diagonal inversa final '\\'. Si el proyecto es la entrada, esta macro equivale a **$(ProjectDir)** .|
|**$(InputExt)**|(Migrado). La extensión de archivo del archivo de entrada. Incluye el "." antes de la extensión de archivo. Si el proyecto es la entrada, esta macro equivale a **$(ProjectExt)** . Para los archivos de código fuente, se trata de **%(Extension)** .|
|**$(InputFileName)**|(Migrado). Nombre del archivo de entrada (definido como nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectFileName)** . Para los archivos de código fuente, se trata de **%(Identity)** .|
|**$(InputName)**|(Migrado). Nombre base del archivo de entrada. Si el proyecto es la entrada, esta macro equivale a **$(ProjectName)** . Para los archivos de código fuente, se trata de **%(Filename)** .|
|**$(InputPath)**|(Migrado). Nombre de la ruta de acceso absoluta del archivo de entrada (definido como unidad + ruta de acceso + nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectPath)** . Para los archivos de código fuente, se trata de **%(FullPath)** .|
|**$(ParentName)**|Nombre del elemento que contiene este elemento de proyecto. Se trata del nombre de la carpeta principal o el nombre de proyecto.|
|**$(SafeInputName)**|El nombre del archivo como un nombre de clase válido, sin extensión de archivo. Esta propiedad no tiene un equivalente exacto.|
|**$(SafeParentName)**|El nombre del elemento primario inmediato con formato de nombre válido. Por ejemplo, un formulario es el elemento primario de un archivo .resx. Esta propiedad no tiene un equivalente exacto.|
|**$(SafeRootNamespace)**|El espacio de nombres en el que los asistentes para proyectos agregarán el código. Este espacio de nombres solo contendrá caracteres que se permitirían en un identificador de C++ válido. Esta propiedad no tiene un equivalente exacto.|

## <a name="see-also"></a>Consulte también

[Proyectos de Visual Studio C++ :](../creating-and-managing-visual-cpp-projects.md)\
[Guía C++ de migración y actualización de Visual](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[Información general sobre posibles problemas de actualización](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
