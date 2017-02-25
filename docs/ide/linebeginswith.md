---
title: "LineBeginsWith | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LineBeginsWith"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LineBeginsWith (método)"
ms.assetid: cbdd08ad-7309-4504-9f23-1c22bb3e4bd0
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# LineBeginsWith
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función a la que llama [InsertIntoFunction](../ide/insertintofunction.md) para determinar si una línea empieza con la cadena especificada.  
  
## Sintaxis  
  
```  
  
      function LineBeginsWith(   
   strBody,   
   strSearchString,   
   nStartPos    
);  
```  
  
#### Parámetros  
 *strBody*  
 Cuerpo de la función.  
  
 `strSearchString`  
 Cadena que se va a buscar.  
  
 *nStartPos*  
 Posición inicial de la búsqueda.  
  
## Valor devuelto  
 **true** si se encuentra una cadena; de lo contrario, **false**.  
  
## Comentarios  
 `InsertIntoFunction` llama a esta función para determinar si la línea especificada comienza con la cadena especificada.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [OffsetToLineNumber](../ide/offsettolinenumber.md)