---
title: "IncludeCodeElementDeclaration | Microsoft Docs"
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
  - "IncludeCodeElementDeclaration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncludeCodeElementDeclaration (método)"
ms.assetid: 714e76e4-76bc-439a-982a-cf9d4ada7677
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IncludeCodeElementDeclaration
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega la instrucción de inclusión a `strInFile`, incluyendo el encabezado donde se implementa `strCodeElemName` \(si es que el encabezado está en `oProj`\).  
  
## Sintaxis  
  
```  
  
      function IncludeCodeElementDeclaration(   
   oProj,   
   strCodeElemName,   
   strInFile    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
 `strCodeElemName`  
 Nombre completo del elemento de código para el que se está buscando el encabezado de definición.  
  
 `strInFile`  
 Archivo que incluirá el encabezado de definición, si es que se encuentra.  
  
## Comentarios  
 Agrega la instrucción de inclusión a `strInFile`, incluyendo el encabezado donde se implementa `strCodeElemName` \(si es que el encabezado está en `oProj`\).  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)