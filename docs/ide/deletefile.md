---
title: "DeleteFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DeleteFile (método)"
ms.assetid: 0cddaedb-8fad-440e-8f18-677fdff94a63
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DeleteFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Elimina el archivo especificado.  
  
## Sintaxis  
  
```  
  
      function DeleteFile(   
   oFSO,   
   strFile    
)   
```  
  
#### Parámetros  
 *oFSO*  
 Objeto del sistema de archivos \(FSO\).  
  
 `strFile`  
 Nombre del archivo que se va a eliminar.  
  
## Comentarios  
 Se llama a esta función para eliminar el archivo especificado.  
  
## Ejemplo  
  
```  
// Declare a temporary file.  
var strFile = strTempFolder + "\\" + strTarget;  
var strClassName = strTarget.split(".");  
wizard.AddSymbol("SAFE_CLASS_NAME", strClassName[0]);  
wizard.AddSymbol("SAFE_ITEM_NAME", strClassName[0]);  
  
// Declare the template name.  
var strTemplate = strTemplatePath + "\\" + strTpl;  
  
// Render and insert the template.  
wizard.RenderTemplate(strTemplate, strFile, bCopyOnly);  
  
// Create a new project file and add the file from the template.  
var projfile = projItems.AddFromTemplate(strFile, strTarget);  
  
// Delete the temporary file from the file structure object.  
DeleteFile(fso, strFile);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)