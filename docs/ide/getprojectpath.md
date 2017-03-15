---
title: "GetProjectPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProjectPath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProjectPath (método)"
ms.assetid: a5e51fe4-c068-47b7-9f2f-1a1d6c71a963
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetProjectPath
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve la ruta de acceso del directorio del proyecto.  
  
## Sintaxis  
  
```  
  
      function GetProjectPath(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Valor devuelto  
 La ruta de acceso del directorio del proyecto.  
  
## Comentarios  
 Se llama a esta función para obtener la ruta de acceso del proyecto.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetProjectFile](../ide/getprojectfile.md)