---
title: "AddFilesToProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddFilesToProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddFilesToProject (método)"
ms.assetid: 3ff11406-bb4a-4eb7-a8df-c655b964ff76
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# AddFilesToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega al proyecto todos los archivos especificados en el archivo Templates.inf.  
  
## Sintaxis  
  
```  
  
      function AddFilesToProject(   
   oProj,   
   strProjectName,   
   InfFile    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
 `strProjectName`  
 Nombre del proyecto.  
  
 *InfFile*  
 Objeto del archivo Templates.inf.  Este archivo contiene una lista de los nombres de archivo creados por el asistente al finalizar.  
  
## Comentarios  
 Llame a esta función para agregar al proyecto todos los archivos enumerados en Templates.inf.  Con esta función puede agregar archivos de recursos, de plantilla o de Ayuda.  
  
## Ejemplo  
  
```  
// Assign the project path and project name.  
var strProjectPath = wizard.FindSymbol("PROJECT_PATH");  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Create the Visual C++ project and call it "MyProj"  
selProj = CreateProject(strProjectName, strProjectPath);  
selProj.Object.Keyword = "MyProj";  
  
// Add common and specific configurations to the project.  
AddCommonConfig(selProj, strProjectName);  
AddSpecificConfig(selProj, strProjectName);  
  
// Set the project filters  
SetFilters(selProj);  
  
// Create the project's Templates.inf file   
var InfFile = CreateInfFile();  
  
// Add the files in Templates.inf to the project.  
AddFilesToProject(selProj, strProjectName, InfFile);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [CreateInfFile](../ide/createinffile.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)