---
title: "GetUniqueFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetUniqueFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUniqueFilename (método)"
ms.assetid: f9760e1a-82d0-4d8b-b00a-6f4c36f6b2c6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# GetUniqueFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve un nombre de archivo único.  
  
## Sintaxis  
  
```  
  
      function GetUniqueFileName(   
   strDirectory,   
   strFileName    
);  
```  
  
#### Parámetros  
 *strDirectory*  
 Directorio en el que buscar el nombre de archivo.  
  
 `strFileName`  
 Nombre de archivo que se va a comprobar.  
  
## Valor devuelto  
 El nombre de archivo indicado en `strFileName`, en caso de que sea único; de lo contrario, la función devolverá `strFileName` anexado con un número comprendido entre 1 y 9999999 para hacerlo único.  Si no se proporciona `strFileName`, esta función devolverá un nombre de archivo único mediante [GetTempName Method](jsmthGetTempName).  
  
## Comentarios  
 Devuelve un nombre de archivo único.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetProjectFile](../ide/getprojectfile.md)