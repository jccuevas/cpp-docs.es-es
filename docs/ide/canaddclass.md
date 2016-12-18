---
title: "CanAddClass | Microsoft Docs"
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
  - "CanAddClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddClass (método)"
ms.assetid: 76739742-1e34-470c-910d-8784f0adfbf0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanAddClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente llama a esta función para comprobar si el proyecto es compatible con el asistente para código que el usuario intenta ejecutar.  
  
## Sintaxis  
  
```  
  
      function CanAddClass(   
   oProj,   
   oObject    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
 `oObject`  
 Objeto seleccionado.  En este caso, el proyecto actual.  
  
## Valor devuelto  
 **true** si se puede agregar la clase; de lo contrario, **false**.  
  
## Comentarios  
 El asistente llama a esta función cuando el parámetro PREPROCESS\_FUNCTION está en el [archivo .vsz de control del proyecto](../ide/dot-vsz-file-project-control.md).  
  
 Comprueba si está disponible el [Modelo de código de Visual C\+\+](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b).  Si el modelo de código no está disponible, la función informará de un error y devolverá **false**.  
  
## Ejemplo  
  
```  
// Determine if a class can be added to the project  
if (CanAddClass(selProj, selObj))  
{  
   return true;  
}  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [CanAddMFCClass](../ide/canaddmfcclass.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)