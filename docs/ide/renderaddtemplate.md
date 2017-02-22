---
title: "RenderAddTemplate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RenderAddTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RenderAddTemplate (método)"
ms.assetid: 84c898d6-8676-4ae1-9245-c023e1c9ab92
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# RenderAddTemplate
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un archivo de plantilla y, opcionalmente, lo agrega al proyecto.  
  
## Sintaxis  
  
```  
  
      function RenderAddTemplate(   
   strTemplateFile,   
   strProjectFile,   
   ProjToAddTo,   
   bOpen    
);  
```  
  
#### Parámetros  
 *strTemplateFile*  
 Nombre del archivo de plantilla \(únicamente el nombre, sin ruta de acceso\), situado en una ruta de acceso relativa a TEMPLATES\_PATH.  
  
 *strProjectFile*  
 Nombre del nuevo archivo creado.  Esta cadena puede incluir la ruta de acceso, pero de forma relativa a PROJECT\_PATH.  
  
 *ProjToAddTo*  
 Objeto del proyecto.  Deberá especificarse el nombre del proyecto si el archivo creado se va a agregar necesariamente al proyecto; de lo contrario, deberá omitirse o pasarse el valor **false**.  
  
 *bOpen*  
 Si su valor es **true**, abrirá el archivo en el editor predeterminado después de agregarlo al proyecto.  
  
## Comentarios  
 Se llama a esta función para representar un archivo de plantilla y, opcionalmente, agregarlo al proyecto.  
  
## Ejemplo  
  
```  
// Declare the project path and the template path.  
var strProjectPath = wizard.FindSymbol("PROJECT_PATH");  
var strTemplatePath = wizard.FindSymbol("TEMPLATES_PATH");  
// Declare the template header and implementation files.  
var strTemplateHeader = wizard.FindSymbol("TEMPLATE_HEADER");  
var strTemplateImpl = wizard.FindSymbol("TEMPLATE_IMPL");  
// Render the template strTemplateHeader and open it in the editor.  
RenderAddTemplate(strTemplateHeader, strHeaderFile, selProj, true);   
// Render the template strTemplateImpl, but do not open it   
// in the editor.  
RenderAddTemplate(strTemplateImpl, strImplFile, selProj, false);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)