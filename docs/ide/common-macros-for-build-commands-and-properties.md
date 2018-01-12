---
title: "Común Macros para propiedades y comandos de compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f96e403516d6f85804fa798d7a0c28575482ff43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="common-macros-for-build-commands-and-properties"></a>Común Macros para propiedades y comandos de compilación
Dependiendo de las opciones de instalación, Visual Studio puede hacer cientos de macros disponibles para usted. Estos se corresponden con las propiedades de MSBuild que se establecen de forma predeterminada, o en los archivos .props o .targets o en la configuración del proyecto. Estas macros pueden usarse en cualquier parte del cuadro de diálogo **Páginas de propiedades** de un proyecto donde se aceptan cadenas. Estas macros no distinguen mayúsculas de minúsculas.  
  
 Para mostrar las macros disponibles actualmente, en la columna situada a la derecha de un nombre de propiedad, haga clic en la flecha de lista desplegable. Si **Editar** está disponible, haga clic en él y luego en el cuadro de diálogo de edición, haga clic en **Macros**. Para obtener más información, vea la sección **Specifying User-Defined Values** de [Páginas de propiedades](../ide/property-pages-visual-cpp.md).  
  
 Las macros que se identifican como "En desuso" se dejaron de usar o se reemplazaron por una [macro de metadatos de elemento](/visualstudio/msbuild/itemmetadata-element-msbuild) equivalente (**%(***nombre***)**). Las macros que se identifican como "En desuso; migrada" también se dejaron de usar. Además, si el proyecto que contiene la macro se migra desde Visual Studio 2008, Visual Studio convierte la macro a la macro equivalente actual.  
  
 En la tabla siguiente describe un subconjunto de uso frecuente de las macros disponibles. Esta lista no es exhaustiva. Para obtener detalles sobre cómo se crean y se utilizan como macros en .props y .targets, archivos .vcxproj definiciones de propiedad de MSBuild, vea [propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
|Macro|Descripción|  
|-----------|-----------------|  
|**$ (RemoteMachine)**|Establece en el valor de la propiedad **Remote Machine** en la página de propiedades de depuración. Para obtener más información, vea [Cambiar la configuración del proyecto para una configuración de depuración de C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|  
|**$(Configuration)**|El nombre de la configuración del proyecto actual (por ejemplo, "Depuración").|  
|**$(Platform)**|El nombre de la plataforma del proyecto actual, por ejemplo, "Win32".|  
|**$ (ParentName)**|(En desuso). Nombre del elemento que contiene este elemento de proyecto. Se trata del nombre de la carpeta principal o el nombre de proyecto.|  
|**RootNamespace**|El espacio de nombres, si hubiera, que contiene la aplicación.|  
|**$(IntDir)**|Ruta de acceso al directorio especificado para los archivos intermedios. Si se trata de una ruta de acceso relativa, los archivos intermedios van a esta ruta de acceso anexado al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Intermediate Directory** . No use **$(OutDir)** para definir esta propiedad.|  
|**$(OutDir)**|Ruta de acceso al directorio del archivo de salida. Si se trata de una ruta de acceso relativa, los archivos de salida van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Output Directory** . No use **$(IntDir)** para definir esta propiedad.|  
|**DevEnvDir**|El directorio de instalación de Visual Studio (definido como unidad + ruta de acceso); incluye la barra diagonal '\\'.|  
|**InputDir**|(En desuso; migrada). El directorio del archivo de entrada (definido como unidad + ruta de acceso); incluye la barra diagonal '\\'. Si el proyecto es la entrada, esta macro equivale a **$(ProjectDir)**.|  
|**InputPath**|(En desuso; migrada). El nombre de ruta de acceso absoluta del archivo de entrada (definido como unidad + ruta de acceso + nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectPath)**.|  
|**$ (InputName)**|(En desuso; migrada). El nombre base del archivo de entrada. Si el proyecto es la entrada, esta macro equivale a **$(ProjectName)**.|  
|**InputFileName**|(En desuso; migrada). El nombre de archivo del archivo de entrada (definido como nombre base + extensión de archivo). Si el proyecto es la entrada, esta macro equivale a **$(ProjectFileName)**.|  
|**InputExt**|(En desuso; migrada). La extensión de archivo del archivo de entrada. Incluye el "." antes de la extensión de archivo. Si el proyecto es la entrada, esta macro equivale a **$(ProjectExt)**.|  
|**$(ProjectDir)**|El directorio del proyecto (definido como unidad + ruta de acceso); incluye la barra diagonal '\\'.|  
|**$(ProjectPath)**|El nombre de ruta de acceso absoluta del proyecto (definido como unidad + ruta de acceso + nombre base + extensión de archivo).|  
|**$(ProjectName)**|El nombre base del proyecto.|  
|**$(ProjectFileName)**|El nombre de archivo del proyecto (definido como nombre base + extensión de archivo).|  
|**$(ProjectExt)**|La extensión de archivo del proyecto. Incluye el "." antes de la extensión de archivo.|  
|**$ (SolutionDir)**|El directorio de la solución (definido como unidad + ruta de acceso); incluye la barra diagonal '\\'. Definida cuando se desea generar una solución en el IDE.|  
|**SolutionPath**|El nombre de ruta de acceso absoluta de la solución (definido como unidad + ruta de acceso + nombre base + extensión de archivo). Definida cuando se desea generar una solución en el IDE.|  
|**SolutionName**|El nombre base de la solución. Definida cuando se desea generar una solución en el IDE.|  
|**SolutionFileName**|El nombre de archivo de la solución (definido como nombre base + extensión de archivo). Definida cuando se desea generar una solución en el IDE.|  
|**SolutionExt**|La extensión de archivo de la solución. Incluye el "." antes de la extensión de archivo. Definida cuando se desea generar una solución en el IDE.|  
|**Targetdir**|El directorio del archivo de salida principal de la generación (definido como unidad + ruta de acceso); incluye la barra diagonal '\\'.|  
|**$ (TargetPath)**|El nombre de ruta de acceso absoluta del archivo de salida principal de la compilación (definido como unidad + ruta de acceso + nombre base + extensión de archivo).|  
|**Problema**|El nombre base del archivo de salida principal de la compilación.|  
|**TargetFileName**|El nombre de archivo del archivo de salida principal de la generación (definido como nombre base + extensión de archivo).|  
|**$(TargetExt)**|La extensión de archivo del archivo de salida principal de la compilación. Incluye el "." antes de la extensión de archivo.|  
|**$(VSInstallDir)**|El directorio en el que instaló Visual Studio.<br /><br /> Esta propiedad contiene la versión de Visual Studio de destino, que podría ser diferente de Visual Studio host. Por ejemplo, al compilar con `$(PlatformToolset) = v110`, **$(VSInstallDir)** contiene la ruta de acceso a la instalación de Visual Studio 2012.|  
|**$(VCInstallDir)**|El directorio en el que instaló Visual C++.<br /><br /> Esta propiedad contiene la versión de Visual C++ de destino, que podría ser diferente de Visual Studio host. Por ejemplo, al compilar con `$(PlatformToolset) = v140`, **VCInstallDir** contiene la ruta de acceso a la instalación de Visual C++ 2015.|  
|**$(FrameworkDir)**|El directorio en el que se instaló .NET Framework.|  
|**FrameworkVersion**|La versión de .NET Framework usada por Visual Studio. Junto con **$(FrameworkDir)**, la ruta de acceso completa a la versión de .NET Framework que usa Visual Studio.|  
|**FrameworkSDKDir**|El directorio en el que instaló .NET Framework. .NET Framework pudo haberse instalado como parte de Visual Studio o por separado.|  
|**WebDeployPath**|La ruta de acceso relativa desde la raíz de la implementación web donde residen las salidas del proyecto. Devuelve el mismo valor que <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|  
|**WebDeployRoot**|La ruta de acceso absoluta a la ubicación de  **\<localhost >**. Por ejemplo, c:\inetpub\wwwroot.|  
|**$(SafeParentName)**|(En desuso). El nombre del elemento primario inmediato con formato de nombre válido. Por ejemplo, un formulario es el elemento primario de un archivo .resx.|  
|**$(SafeInputName)**|(En desuso). El nombre del archivo como un nombre de clase válido, sin extensión de archivo.|  
|**SafeRootNamespace**|(En desuso). El espacio de nombres en el que los asistentes para proyectos agregarán el código. Este espacio de nombres solo contendrá caracteres que se permitirían en un identificador de C++ válido.|  
|**FXCOPDIR**|La ruta de acceso al archivo fxcop.cmd. El archivo fxcop.cmd no se instala con todas las ediciones de Visual C++.|  
  
## <a name="see-also"></a>Vea también  
 [Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)