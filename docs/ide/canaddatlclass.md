---
title: "CanAddATLClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanAddATLClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddATLClass (método)"
ms.assetid: 7a8abf90-c1b8-475c-af22-7948478084f9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CanAddATLClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente llama a esta función para comprobar si el usuario puede agregar una clase ATL al proyecto.  
  
## Sintaxis  
  
```  
  
      function CanAddATLClass(   
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
 **true** si se puede agregar la clase; **false** si el usuario llama a la función para un proyecto que no es un proyecto ATL ni es compatible con ATL.  
  
## Comentarios  
 El asistente llama a esta función para comprobar si el proyecto es compatible con el asistente para código que va a ejecutarse \(es decir, si puede aceptar una clase ATL\).  
  
 El asistente llama a esta función cuando el parámetro PREPROCESS\_FUNCTION está en el [archivo .vsz de control del proyecto](../ide/dot-vsz-file-project-control.md) y comprueba si el [Modelo de código de Visual C\+\+](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b) está disponible.  Si el modelo de código no está disponible, la función informará de un error y devolverá **false**.  
  
## Ejemplo  
  
```  
// Determine if an ATL class can be added to the project  
if (CanAddATLClass(selProj, selObj))  
{  
   return true;  
}  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [CanAddClass](../ide/canaddclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)   
 [CanAddMFCClass](../ide/canaddmfcclass.md)