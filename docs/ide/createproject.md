---
title: "CreateProject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateProject (método)"
ms.assetid: b5598b46-fe29-4ad0-8bfe-a4dc789aeebd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreateProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un proyecto de C\+\+.  
  
## Sintaxis  
  
```  
  
      function CreateProject(   
   strProjectName,   
   strProjectPath    
);  
```  
  
#### Parámetros  
 `strProjectName`  
 Cadena que contiene el nombre del proyecto.  
  
 *strProjectPath*  
 Cadena que contiene la ruta de acceso del proyecto.  
  
## Valor devuelto  
 Objeto del proyecto.  
  
## Comentarios  
 Se llama a esta función para crear un proyecto de C\+\+ que se pueda abrir en Visual Studio.  Si se especifica el parámetro de contexto **WizardType** del asistente como **vsWizardAddSubProject**, el proyecto se agregará al proyecto existente como subproyecto.  Para obtener más información, vea [ContextParams \(Enumeración\)](../Topic/Context%20Parameters%20for%20Launching%20Wizards.md).  
  
## Ejemplo  
 Vea [AddFilesToProject](../ide/addfilestoproject.md).  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)