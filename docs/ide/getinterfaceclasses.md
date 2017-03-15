---
title: "GetInterfaceClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetInterfaceClasses"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceClasses (método)"
ms.assetid: 712c112f-b4ff-43c4-ad49-c4f4c13c48bd
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetInterfaceClasses
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve el objeto `VCCodeClass` asociado a una interfaz.  
  
## Sintaxis  
  
```  
  
      function GetInterfaceClasses(   
   strInterface,   
   oProject,   
   aryClasses    
);  
```  
  
#### Parámetros  
 *strInterface*  
 Nombre de la interfaz que contiene los objetos de clase.  
  
 *oProject*  
 Proyecto seleccionado.  
  
 *aryClasses*  
 \[out\] Matriz de objetos de clase de la interfaz.  
  
## Valor devuelto  
 El objeto <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeClass> asociado a una interfaz.  
  
## Comentarios  
 Se llama a esta función para recuperar las clases asociadas a una interfaz.  
  
## Ejemplo  
  
```  
var aryClasses = new Array();  
GetInterfaceClasses(oInterface.Name, selProj, aryClasses);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetInterfaceType](../ide/getinterfacetype.md)