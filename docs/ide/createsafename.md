---
title: "CreateSafeName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateSafeName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateSafeName (método)"
ms.assetid: 3a0dd4af-776d-4c25-aff9-4c539f173cb8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CreateSafeName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera un nombre descriptivo de C\+\+.  
  
## Sintaxis  
  
```  
  
      function CreateSafeName(   
   strName    
);  
```  
  
#### Parámetros  
 `strName`  
 Nombre antiguo.  
  
## Valor devuelto  
 Nombre nuevo \(seguro\).  
  
## Comentarios  
 Se llama a esta función para crear un nombre descriptivo de C\+\+ a partir de un nombre que contenga caracteres que C\+\+ no pueda utilizar.  Los nombres aceptados por C\+\+ pueden contener letras mayúsculas o minúsculas, dígitos o un carácter de subrayado \("\_"\).  
  
 Esta función comprueba el nombre antiguo carácter a carácter, omitiendo los caracteres que no se puedan utilizar.  Si el nombre antiguo no contiene caracteres descriptivos, la función devolverá el nuevo nombre como "My".  Si el nuevo nombre descriptivo empieza con un dígito, la función agregará "My" al nuevo nombre.  
  
## Ejemplo  
  
```  
// Get the project name  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Set the project name to the safe project name.   
var strSafeProjectName = CreateSafeName(strProjectName);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)