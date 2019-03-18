---
title: Macros comunes para propiedades y comandos de compilación
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
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
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 669114691bc89c1e8136e07a949be57cda3d71b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826645"
---
# <a name="common-macros-for-build-commands-and-properties"></a>Macros comunes para propiedades y comandos de compilación

Según las opciones de instalación, Visual Studio puede poner a su disposición cientos de macros. Se corresponden con las propiedades de MSBuild que se establecen de forma predeterminada, o en los archivos .props o .targets, o bien en la configuración del proyecto. Estas macros pueden usarse en cualquier parte del cuadro de diálogo **Páginas de propiedades** de un proyecto donde se aceptan cadenas. Estas macros no distinguen mayúsculas de minúsculas.

## <a name="view-the-current-properties-and-macros"></a>Ver las propiedades y macros actuales

Para mostrar las macros disponibles actualmente, en cualquier página de propiedades del cuadro de diálogo **Páginas de propiedades**, haga clic en la flecha desplegable situada al final de una fila de propiedad. Si **Editar** está disponible, seleccione esa opción y luego en el cuadro de diálogo de edición, haga clic en el botón **Macros**. El conjunto actual de propiedades y macros visibles para Visual Studio se muestra junto con el valor actual para cada una. Para obtener más información, consulte el **Specifying User-Defined valores** sección de [referencia de página de propiedades de proyecto de C++](property-pages-visual-cpp.md).

## <a name="list-of-common-macros"></a>Lista de macros comunes

En esta tabla se describe un subconjunto de uso frecuente de las macros disponibles. Esta lista está muy lejos de ser exhaustiva. Para obtener detalles sobre cómo se crean y usan las definiciones de propiedades de MSBuild como macros en los archivos .props, .targets y .vcxproj, vea [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Descripción|
|-----------|-----------------|
|**$(Configuration)**|El nombre de la configuración del proyecto actual (por ejemplo, "Depuración").|
|**$(DevEnvDir)**|El directorio de instalación de Visual Studio (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\".|
|**$(FrameworkDir)**|El directorio en el que se instaló .NET Framework.|
|**$(FrameworkSDKDir)**|El directorio en el que instaló .NET Framework. .NET Framework pudo haberse instalado como parte de Visual Studio o por separado.|
|**$(FrameworkVersion)**|La versión de .NET Framework usada por Visual Studio. Junto con **$(FrameworkDir)**, la ruta de acceso completa a la versión de .NET Framework que usa Visual Studio.|
|**$(FxCopDir)**|La ruta de acceso al archivo fxcop.cmd. El archivo fxcop.cmd no se instala con todas las ediciones de Visual C++.|
|**$(IntDir)**|Ruta de acceso al directorio especificado para los archivos intermedios. Si se trata de una ruta de acceso relativa, los archivos intermedios van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Intermediate Directory** . No use **$(OutDir)** para definir esta propiedad.|
|**$(OutDir)**|Ruta de acceso al directorio del archivo de salida. Si se trata de una ruta de acceso relativa, los archivos de salida van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Output Directory** . No use **$(IntDir)** para definir esta propiedad.|
|**$(Platform)**|El nombre de la plataforma del proyecto actual, por ejemplo, "Win32".|
|**$(ProjectDir)**|El directorio del proyecto (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\".|
|**$(ProjectExt)**|La extensión de archivo del proyecto. Incluye el "." antes de la extensión de archivo.|
|**$(ProjectFileName)**|El nombre de archivo del proyecto (definido como nombre base + extensión de archivo).|
|**$(ProjectName)**|El nombre base del proyecto.|
|**$(ProjectPath)**|El nombre de ruta de acceso absoluta del proyecto (definido como unidad + ruta de acceso + nombre base + extensión de archivo).|
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
|**$(VCInstallDir)**|El directorio en el que se incluye el contenido de C++ de la instalación de Visual Studio. Esta propiedad contiene la versión del conjunto de herramientas de Visual C++ de destino, que podría ser diferente a la del host de Visual Studio. Por ejemplo, al compilar con `$(PlatformToolset) = v140`, **$(VCInstallDir)** contiene la ruta de acceso a la instalación de Visual C++ 2015.|
|**$(VSInstallDir)**|El directorio en el que instaló Visual Studio. Esta propiedad contiene la versión del conjunto de herramientas de Visual Studio de destino, que podría ser diferente a la del host de Visual Studio. Por ejemplo, al compilar con `$(PlatformToolset) = v110`, **$(VSInstallDir)** contiene la ruta de acceso a la instalación de Visual Studio 2012.|
|**$(WebDeployPath)**|La ruta de acceso relativa desde la raíz de la implementación web donde residen las salidas del proyecto. Devuelve el mismo valor que <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(WebDeployRoot)**|La ruta de acceso absoluta a la ubicación de **\<localhost>**. Por ejemplo, c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Macros obsoletas

El sistema de compilación de C++ se ha cambiado significativamente entre Visual Studio 2008 y Visual Studio 2010. Muchas macros que se usaban en los tipos de proyectos anteriores se han cambiado por otras nuevas. Estas macros ya no se usan o se han reemplazado por una o varias propiedades equivalentes o valores de [macro de metadatos de elemento](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_nombre_**)**). Las macros que se marcan como "migradas" se pueden actualizar mediante la herramienta de migración de proyectos. Si el proyecto que contiene la macro se migra desde Visual Studio 2008 o una versión anterior a Visual Studio 2010, Visual Studio convierte la macro a la macro equivalente actual. En las versiones posteriores de Visual Studio no se pueden convertir proyectos de Visual Studio 2008 y versiones anteriores al nuevo tipo de proyecto. Debe convertir estos proyectos en dos pasos: en primer lugar convertirlos a Visual Studio 2010 y, después, convertir el resultado a la versión más reciente de Visual Studio. Para obtener más información, vea [Información general sobre posibles problemas de actualización](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Descripción|
|-----------|-----------------|
|**$(InputDir)**|(Migrada). El directorio del archivo de entrada (definido como unidad + ruta de acceso); incluye la barra diagonal inversa "\\". Si el proyecto es la entrada, esta macro equivale a **$(ProjectDir)**.|
|**$(InputExt)**|(Migrada). La extensión de archivo del archivo de entrada. Incluye el "." antes de la extensión de archivo. Si el proyecto es la entrada, esta macro equivale a **$(ProjectExt)**. Para los archivos de código fuente, se trata de **%(Extension)**.|
|**$(InputFileName)**|(Migrada). El nombre de archivo del archivo de entrada (definido como nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectFileName)**. Para los archivos de código fuente, se trata de **%(Identity)**.|
|**$(InputName)**|(Migrada). El nombre base del archivo de entrada. Si el proyecto es la entrada, esta macro equivale a **$(ProjectName)**. Para los archivos de código fuente, se trata de **%(Filename)**.|
|**$(InputPath)**|(Migrada). El nombre de ruta de acceso absoluta del archivo de entrada (definido como unidad + ruta de acceso + nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectPath)**. Para los archivos de código fuente, se trata de **%(FullPath)**.|
|**$(ParentName)**|Nombre del elemento que contiene este elemento de proyecto. Se trata del nombre de la carpeta principal o el nombre de proyecto.|
|**$(SafeInputName)**|El nombre del archivo como un nombre de clase válido, sin extensión de archivo. Esta propiedad no tiene un equivalente exacto.|
|**$(SafeParentName)**|El nombre del elemento primario inmediato con formato de nombre válido. Por ejemplo, un formulario es el elemento primario de un archivo .resx. Esta propiedad no tiene un equivalente exacto.|
|**$(SafeRootNamespace)**|El espacio de nombres en el que los asistentes para proyectos agregarán el código. Este espacio de nombres solo contendrá caracteres que se permitirían en un identificador de C++ válido. Esta propiedad no tiene un equivalente exacto.|

## <a name="see-also"></a>Vea también

- [Proyectos de Visual Studio - C++](../creating-and-managing-visual-cpp-projects.md)
- [Guía de migración y actualización de Visual C++](../../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Información general sobre posibles problemas de actualización](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
