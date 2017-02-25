---
title: "GetInterfaceType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetInterfaceType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceType (método)"
ms.assetid: cc6403a8-0c2b-47f7-a8f7-9db95df87d5a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetInterfaceType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el tipo de interfaz.  
  
## Sintaxis  
  
```  
  
      function GetInterfaceType(   
   oInterface    
);  
```  
  
#### Parámetros  
 *oInterface*  
 Un objeto <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface>.  
  
## Valor devuelto  
 La cadena que indica el tipo de interfaz \(por ejemplo, personalizada, dual, dispinterface u oleautomation\).  
  
## Comentarios  
 Se llama a esta función para obtener el tipo de interfaz.  
  
## Ejemplo  
 Vea [GetMaxID](../ide/getmaxid.md).  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetInterfaceClasses](../ide/getinterfaceclasses.md)