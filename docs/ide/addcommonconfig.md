---
title: "AddCommonConfig | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddCommonConfig"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddCommonConfig (método)"
ms.assetid: 16abad93-6dd0-4daa-bf76-91eb6ffbdffa
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# AddCommonConfig
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega las configuraciones predeterminadas al proyecto.  
  
## Sintaxis  
  
```  
  
      function AddCommonConfig(   
   oProj,   
   strProjectName    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
 `strProjectName`  
 Nombre del proyecto.  
  
## Comentarios  
 Se llama a esta función para agregar las configuraciones predeterminadas del modelo de código al proyecto que crea el asistente.  Puede especificarse una configuración de versión de lanzamiento o de versión de depuración.  En las siguientes tablas, se detallan los valores predeterminados de las propiedades del objeto de modelo de código para cada tipo de configuración.  
  
### Objeto del compilador de Visual C\+\+  
  
|Propiedad del objeto|Valores de configuración de lanzamiento|Configuración de la versión de depuración|  
|--------------------------|---------------------------------------------|-----------------------------------------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>|pchUseUsingSpecific|pchUseUsingSpecific|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>|3|3|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>|No es aplicable|true|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>|debugEnabled|debugEditAndContinue|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>|optimizeMaxSpeed|No es aplicable|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A>|No es aplicable|runtimeBasicCheckAll|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>|true|true|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>|true|No es aplicable|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>|true|No es aplicable|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>|true|No es aplicable|  
  
### Objeto de configuración de Visual C\+\+  
  
|Propiedad del objeto|Valores de configuración de lanzamiento|Configuración de la versión de depuración|  
|--------------------------|---------------------------------------------|-----------------------------------------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>|"Release"|"Debug"|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>|"Release"|"Debug"|  
  
### Objeto del vinculador de Visual C\+\+  
  
|Propiedad del objeto|Valores de configuración de lanzamiento|Configuración de la versión de depuración|  
|--------------------------|---------------------------------------------|-----------------------------------------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>|subSystemWindows|subSystemWindows|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>|machineX86|machineX86|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>|true|true|  
  
## Ejemplo  
  
```  
// Create the Visual C++ project.  
selProj = CreateProject(strProjectName, strProjectPath);  
// Add the common configuration to the project.  
   AddCommonConfig(selProj, strProjectName);  
   selProj.Object.keyword = "MyProj";  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)