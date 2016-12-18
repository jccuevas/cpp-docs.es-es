---
title: "IsATLProject | Microsoft Docs"
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
  - "IsATLProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsATLProject (método)"
ms.assetid: 811115af-5bcd-4ce2-a514-34de4c7419ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsATLProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si el proyecto se basa en ATL.  
  
## Sintaxis  
  
```  
  
      function IsATLProject(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Valor devuelto  
 **true** si se trata de un proyecto ATL; de lo contrario, **false**.  
  
## Comentarios  
 Indica si el proyecto se basa en ATL.  
  
## Ejemplo  
  
```  
function CanAddATLSupport(selProj, selObj)  
{  
   if (IsATLProject(selProj))  
   {  
      var L_ErrMsg1_Text = "Current project already has ATL support.";  
      wizard.ReportError(L_ErrMsg1_Text);  
      return false;  
   }  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [IsAttributedProject](../ide/isattributedproject.md)