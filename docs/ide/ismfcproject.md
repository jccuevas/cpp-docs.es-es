---
title: "IsMFCProject | Microsoft Docs"
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
  - "IsMFCProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsMFCProject (método)"
ms.assetid: 98dd57df-9fdb-40d7-afcf-4b99e9d54dad
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsMFCProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si un proyecto se basa en MFC.  
  
## Sintaxis  
  
```  
  
      function IsMFCProject(   
   oProj,   
   bCWinAppRequired    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
 *bCWinAppRequired*  
 Indica si los archivos con extensión DLL se incluyen en la comprobación.  
  
## Valor devuelto  
 **true** si se trata de un proyecto MFC; de lo contrario, **false**.  
  
## Comentarios  
 Esta función se utiliza para determinar si el proyecto seleccionado es un proyecto MFC.  
  
## Ejemplo  
  
```  
if (!IsMFCProject(selProj, true))  
   {  
      if (gbExceptionThrown)  
         return false;  
      var L_ErrMsg2_Text = "ATL support can only be added to MFC EXEs or MFC Regular DLLs.";  
      wizard.ReportError(L_ErrMsg2_Text);  
      return false;  
   }  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [IsATLProject](../ide/isatlproject.md)   
 [IsAttributedProject](../ide/isattributedproject.md)