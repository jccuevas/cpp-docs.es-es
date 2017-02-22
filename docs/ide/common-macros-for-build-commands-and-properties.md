---
title: "Macros para propiedades y comandos de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "$(ConfigurationName): macro"
  - "$(DevEnvDir): macro"
  - "$(FrameworkDir): macro"
  - "$(FrameworkSDKDir): macro"
  - "$(FrameworkVersion): macro"
  - "$(FxCopDir): macro"
  - "$(Inherit): macro"
  - "$(InputDir): macro"
  - "$(InputExt): macro"
  - "$(InputFileName): macro"
  - "$(InputName): macro"
  - "$(InputPath): macro"
  - "$(IntDir): macro"
  - "$(NoInherit): macro"
  - "$(OutDir): macro"
  - "$(ParentName): macro"
  - "$(PlatformName): macro"
  - "$(ProjectDir): macro"
  - "$(ProjectExt): macro"
  - "$(ProjectFileName): macro"
  - "$(ProjectName): macro"
  - "$(ProjectPath): macro"
  - "$(References): macro"
  - "$(RemoteMachine): macro"
  - "$(RootNamespace): macro"
  - "$(SafeRootNamespace): macro"
  - "$(SolutionDir): macro"
  - "$(SolutionExt): macro"
  - "$(SolutionFileName): macro"
  - "$(SolutionName): macro"
  - "$(SolutionPath): macro"
  - "$(StopEvaluating): macro"
  - "$(TargetDir): macro"
  - "$(TargetExt): macro"
  - "$(TargetFileName): macro"
  - "$(TargetName): macro"
  - "$(TargetPath): macro"
  - "$(VCInstallDir): macro"
  - "$(VSInstallDir): macro"
  - "$(WebDeployPath): macro"
  - "$(WebDeployRoot): macro"
  - "macros de compilación [C++]"
  - "compilaciones [C++], macros"
  - "macro ConfigurationName: $(ConfigurationName)"
  - "macro DevEnvDir: $(DevEnvDir)"
  - "macro FrameworkDir: $(FrameworkDir)"
  - "macro FrameworkSDKDir: $(FrameworkSDKDir)"
  - "macro FrameworkVersion: $(FrameworkVersion)"
  - "macro FxCopDir: $(FxCopDir)"
  - "macro Inherit: $(Inherit)"
  - "macro InputDir: $(InputDir)"
  - "macro InputExt: $(InputExt)"
  - "macro InputFileName: $(InputFileName)"
  - "macro InputName: $(InputName)"
  - "macro InputPath: $(InputPath)"
  - "macro IntDir: $(IntDir)"
  - "macros [C++], macros de compilación"
  - "macro NoInherit: $(NoInherit)"
  - "macro OutDir: $(OutDir)"
  - "macro ParentName: $(ParentName)"
  - "macro PlatformName: $(PlatformName)"
  - "macro ProjectDir: $(ProjectDir)"
  - "macro ProjectExt: $(ProjectExt)"
  - "macro ProjectFileName: $(ProjectFileName)"
  - "macro ProjectName: $(ProjectName)"
  - "macro ProjectPath: $(ProjectPath)"
  - "propiedades [C++], macros de propiedades de compilación"
  - "macro References: $(References)"
  - "macro RemoteMachine: $(RemoteMachine)"
  - "macro RootNamespace: $(RootNamespace)"
  - "macro SafeRootNamespace: $(SafeRootNamespace)"
  - "macro SolutionDir: $(SolutionDir)"
  - "macro SolutionExt: $(SolutionExt)"
  - "macro SolutionFileName: $(SolutionFileName)"
  - "macro SolutionName: $(SolutionName)"
  - "macro SolutionPath: $(SolutionPath)"
  - "macro StopEvaluating: $(StopEvaluating)"
  - "macro TargetDir: $(TargetDir)"
  - "macro TargetExt: $(TargetExt)"
  - "macro TargetFileName: $(TargetFileName)"
  - "macro TargetName: $(TargetName)"
  - "macro TargetPath: $(TargetPath)"
  - "macro VCInstallDir: $(VCInstallDir)"
  - "macro VSInstallDir: $(VSInstallDir)"
  - "macro WebDeployPath: $(WebDeployPath)"
  - "macro WebDeployRoot: $(WebDeployRoot)"
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# Macros para propiedades y comandos de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas macros pueden usarse en cualquier parte del cuadro de diálogo **Páginas de propiedades** de un proyecto donde se aceptan cadenas. Estas macros no distinguen mayúsculas de minúsculas.  
  
 Para mostrar las macros disponibles actualmente, en la columna situada a la derecha de un nombre de propiedad, haga clic en la flecha de lista desplegable. Si **Editar** está disponible, haga clic en él y luego en el cuadro de diálogo de edición, haga clic en **Macros**. Para obtener más información, vea la sección **Specifying User\-Defined Values** de [Páginas de propiedades](../ide/property-pages-visual-cpp.md).  
  
 Las macros que se identifican como "En desuso" se dejaron de usar o se reemplazaron por una [macro de metadatos de elemento](../Topic/ItemMetadata%20Element%20\(MSBuild\).md) equivalente \(**%\(***nombre***\)**\). Las macros que se identifican como "En desuso; migrada" también se dejaron de usar. Además, si el proyecto que contiene la macro se migra desde Visual Studio 2008, Visual Studio convierte la macro a la macro equivalente actual.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|**$\(RemoteMachine\)**|Establece en el valor de la propiedad **Remote Machine**  en la página de propiedades de depuración. Para obtener más información, vea [Cambiar la configuración del proyecto para una configuración de depuración de C\/C\+\+](../Topic/Project%20Settings%20for%20a%20C++%20Debug%20Configuration.md).|  
|**$\(Configuration\)**|El nombre de la configuración del proyecto actual \(por ejemplo, "Depuración"\).|  
|**$\(Platform\)**|El nombre de la plataforma del proyecto actual \(por ejemplo, "Win32"\).|  
|**$\(ParentName\)**|\(En desuso\). Nombre del elemento que contiene este elemento de proyecto. Se trata del nombre de la carpeta principal o el nombre de proyecto.|  
|**$\(RootNameSpace\)**|El espacio de nombres, si hubiera, que contiene la aplicación.|  
|**$\(IntDir\)**|Ruta de acceso al directorio especificado para los archivos intermedios. Si se trata de una ruta de acceso relativa, los archivos intermedios van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Intermediate Directory**. No use **$\(OutDir\)** para definir esta propiedad.|  
|**$\(OutDir\)**|Ruta de acceso al directorio del archivo de salida. Si se trata de una ruta de acceso relativa, los archivos de salida van a esta ruta de acceso anexados al directorio del proyecto. Esta ruta de acceso debe tener una barra diagonal final. Se resuelve en el valor de la propiedad **Output Directory**. No use **$\(IntDir\)** para definir esta propiedad.|  
|**$\(DevEnvDir\)**|El directorio de instalación de Visual Studio \(definido como unidad \+ ruta de acceso; incluye la barra diagonal inversa "\\".|  
|**$\(InputDir\)**|\(En desuso; migrada\). El directorio del archivo de entrada \(definido como unidad \+ ruta de acceso\); incluye la barra diagonal inversa "\\". Si el proyecto es la entrada, esta macro equivale a **$\(ProjectDir\)**.|  
|**$\(InputPath\)**|\(En desuso; migrada\). El nombre de ruta de acceso absoluta del archivo de entrada \(definido como unidad \+ ruta de acceso \+ nombre base \+ extensión de archivo\). Si el proyecto es la entrada, esta macro equivale a **$\(ProjectPath\)**.|  
|**$\(InputName\)**|\(En desuso; migrada\). El nombre base del archivo de entrada. Si el proyecto es la entrada, esta macro equivale a **$\(ProjectName\)**.|  
|**$\(InputFileName\)**|\(En desuso; migrada\). El nombre de archivo del archivo de entrada \(definido como nombre base \+ extensión de archivo\). Si el proyecto es la entrada, esta macro equivale a **$\(ProjectFileName\)**.|  
|**$\(InputExt\)**|\(En desuso; migrada\). La extensión de archivo del archivo de entrada. Incluye el "." antes de la extensión de archivo. Si el proyecto es la entrada, esta macro equivale a **$\(ProjectExt\)**.|  
|**$\(ProjectDir\)**|El directorio del proyecto \(definido como unidad \+ ruta de acceso\); incluye la barra diagonal inversa "\\".|  
|**$\(ProjectPath\)**|El nombre de ruta de acceso absoluta del proyecto \(definido como unidad \+ ruta de acceso \+ nombre base \+ extensión de archivo\).|  
|**$\(ProjectName\)**|El nombre base del proyecto.|  
|**$\(ProjectFileName\)**|El nombre de archivo del proyecto \(definido como nombre base \+ extensión de archivo\).|  
|**$\(ProjectExt\)**|La extensión de archivo del proyecto. Incluye el "." antes de la extensión de archivo.|  
|**$\(SolutionDir\)**|El directorio de la solución \(definido como unidad \+ ruta de acceso\); incluye la barra diagonal inversa "\\".|  
|**$\(SolutionPath\)**|El nombre de ruta de acceso absoluta de la solución \(definido como unidad \+ ruta de acceso \+ nombre base \+ extensión de archivo\).|  
|**$\(SolutionName\)**|El nombre base de la solución.|  
|**$\(SolutionFileName\)**|El nombre de archivo de la solución \(definido como nombre base \+ extensión de archivo\).|  
|**$\(SolutionExt\)**|La extensión de archivo de la solución. Incluye el "." antes de la extensión de archivo.|  
|**$\(TargetDir\)**|El directorio del archivo de salida principal de la compilación \(definido como unidad \+ ruta de acceso\); incluye la barra diagonal inversa "\\".|  
|**$\(TargetPath\)**|El nombre de ruta de acceso absoluta del archivo de salida principal de la compilación \(definido como unidad \+ ruta de acceso \+ nombre base \+ extensión de archivo\).|  
|**$\(TargetName\)**|El nombre base del archivo de salida principal de la compilación.|  
|**$\(TargetFileName\)**|El nombre de archivo del archivo de salida principal de la generación \(definido como nombre base \+ extensión de archivo\).|  
|**$\(TargetExt\)**|La extensión de archivo del archivo de salida principal de la compilación. Incluye el "." antes de la extensión de archivo.|  
|**$\(VSInstallDir\)**|El directorio en el que instaló Visual Studio.<br /><br /> Esta propiedad contiene la versión de Visual Studio de destino, que podría ser diferente de Visual Studio host. Por ejemplo, al compilar con `$(PlatformToolset) = v110`, **$\(VSInstallDir\)** contiene la ruta de acceso a la instalación de Visual Studio 2012.|  
|**$\(VCInstallDir\)**|El directorio en el que instaló Visual C\+\+.<br /><br /> Esta propiedad contiene la versión de Visual C\+\+ de destino, que podría ser diferente de Visual Studio host. Por ejemplo, al compilar con `$(PlatformToolset) = v90`, **$\(VCInstallDir\)** contiene la ruta de acceso a la instalación de Visual C\+\+ 2008.|  
|**$\(FrameworkDir\)**|El directorio en el que se instaló .NET Framework.|  
|**$\(FrameworkVersion\)**|La versión de .NET Framework usada por Visual Studio. Junto con **$\(FrameworkDir\)**, la ruta de acceso completa a la versión de .NET Framework que usa Visual Studio.|  
|**$\(FrameworkSDKDir\)**|El directorio en el que instaló .NET Framework. .NET Framework pudo haberse instalado como parte de Visual Studio o por separado.|  
|**$\(WebDeployPath\)**|La ruta de acceso relativa desde la raíz de la implementación web donde residen las salidas del proyecto. Devuelve el mismo valor que <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|  
|**$\(WebDeployRoot\)**|La ruta de acceso absoluta a la ubicación de **\<localhost\>**. Por ejemplo, c:\\inetpub\\wwwroot.|  
|**$\(SafeParentName\)**|\(En desuso\). El nombre del elemento primario inmediato con formato de nombre válido. Por ejemplo, un formulario es el elemento primario de un archivo .resx.|  
|**$\(SafeInputName\)**|\(En desuso\). El nombre del archivo como un nombre de clase válido, sin extensión de archivo.|  
|**$\(SafeRootNamespace\)**|\(En desuso\). El espacio de nombres en el que los asistentes para proyectos agregarán el código. Este espacio de nombres solo contendrá caracteres que se permitirían en un identificador de C\+\+ válido.|  
|**$\(FxCopDir\)**|La ruta de acceso al archivo fxcop.cmd. El archivo fxcop.cmd no se instala con todas las ediciones de Visual C\+\+.|  
  
## Vea también  
 [Compilar proyectos de C\+\+ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)