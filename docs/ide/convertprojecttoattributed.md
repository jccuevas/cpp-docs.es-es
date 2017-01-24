---
title: "ConvertProjectToAttributed | Microsoft Docs"
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
  - "ConvertProjectToAttributed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertProjectToAttributed (método)"
ms.assetid: 56a2d6e1-7e8e-4595-b2be-ade026593798
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ConvertProjectToAttributed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte un proyecto ATL sin atributos en un proyecto con atributos.  
  
## Sintaxis  
  
```  
  
function ConvertProjectToAttributed( );  
  
```  
  
## Valor devuelto  
 **true** si el proyecto se convirtió correctamente; de lo contrario, **false**.  
  
## Comentarios  
 Se llama a esta función para convertir un proyecto ATL sin atributos en un proyecto ATL con atributos.  Para obtener más información, vea [Programación con atributos](../windows/attributed-programming-concepts.md).  
  
## Ejemplo  
  
```  
// Create a function called CheckAddtoProject.  
function CheckAddtoProject(oProj)  
{  
// Is the project attributed already?  
   try  
   {  
      if (!IsAttributedProject(wizard))  
      {  
         // If the project is not converted to attributed, return false.  
         if (!ConvertProjectToAttributed(oProj))  
            return false;  
      }  
   }  
   catch (e)  
   {  
      var L_ErrMsg1_Text = "Error in CheckAddtoProject: ";  
      wizard.ReportError( L_ErrMsg1_Text + e.description);  
      return false;  
   }  
  
   return true;  
}  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [CanAddNonAttributed](../ide/canaddnonattributed.md)