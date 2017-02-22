---
title: "InsertIntoFunction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InsertIntoFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InsertIntoFunction (método)"
ms.assetid: 50500c3c-bee3-4a9c-a403-7dcd752de23c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# InsertIntoFunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función utilizada por [AddATLSupportToProject](../ide/addatlsupporttoproject.md) para insertar código en [InitInstance](../Topic/CWinApp::InitInstance.md).  
  
## Sintaxis  
  
```  
  
      function InsertIntoFunction(   
   oFunction,   
   strSearchString,   
   nStartLine,   
   nEndLine,   
   bInsideIfBlock    
);  
```  
  
#### Parámetros  
 *oFunction*  
 Objeto de función en el que se realiza la inserción.  
  
 `strSearchString`  
 Cadena que se va a buscar para determinar el punto de inserción.  
  
 *nStartLine*  
 Línea inicial que se pasa a [GetCodeForInitInstance](../ide/getcodeforinitinstance.md).  
  
 *nEndLine*  
 Línea final que se pasa a [GetCodeForInitInstance](../ide/getcodeforinitinstance.md).  
  
 *bInsideIfBlock*  
 Indica si la inserción está en un bloque de función.  
  
## Valor devuelto  
 **true** si es correcto; de lo contrario, **false**.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetMemberfunction](../ide/getmemberfunction.md)