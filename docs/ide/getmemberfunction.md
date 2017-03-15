---
title: "GetMemberfunction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMemberFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMemberfunction (método)"
ms.assetid: 1e610977-9bc7-4ff2-a79f-132c8e913b4d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetMemberfunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se llama a esta función para obtener un objeto de función a partir del nombre especificado.  
  
## Sintaxis  
  
```  
  
      function GetMemberfunction(   
   oClass,   
   strFuncName,   
   oProj    
);  
```  
  
#### Parámetros  
 *oClass*  
 Objeto de clase seleccionado.  
  
 `strFuncName`  
 Nombre de la función que se va a recuperar.  
  
 `oProj`  
 Proyecto seleccionado.  
  
## Valor devuelto  
 La función indicada por `strFuncName`.  
  
## Comentarios  
 Se llama a esta función para obtener un objeto de función a partir del nombre especificado.  Vea <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeModel.Functions%2A>, en el modelo de código de Visual C\+\+ para obtener más información.  
  
## Ejemplo  
  
```  
// Gets the function ExitInstance from the class CWinApp in the   
// current project.  
var oExitInstance = GetMemberFunction(oCWinApp, "ExitInstance", oProj);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)