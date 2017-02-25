---
title: "OffsetToLineNumber | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OffsetToLineNumber"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OffsetToLineNumber (función)"
ms.assetid: ac7e3c22-6b3b-432c-85cc-b50bbef9ce8c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OffsetToLineNumber
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función a la que llama [InsertIntoFunction](../ide/insertintofunction.md) para convertir en un número de línea un índice dentro del cuerpo de una función.  
  
## Sintaxis  
  
```  
  
      function OffsetToLineNumber(   
   strString,   
   nPos    
);  
```  
  
#### Parámetros  
 `strString`  
 Cadena que contiene el cuerpo de la función.  El cuerpo de la función es una cadena de varias líneas delimitadas por pares de caracteres de retorno de carro y avance de línea.  
  
 `nPos`  
 Posición dentro de la cadena.  
  
## Valor devuelto  
 La línea, dentro del cuerpo de la función, en que se encuentra `nPos`.  Se considera que la primera línea de la función es la línea 1, no la 0.  
  
## Comentarios  
 Busca el número de línea de una posición determinada dentro del cuerpo de una función.  
  
 `InsertIntoFunction` llama a esta función para convertir en un número de línea el índice situado en `nPos`, dentro del cuerpo de una función.  
  
## Ejemplo  
  
```  
strString = "function DelFile(fso,  
 strWizTempFile)\r\n{\r\n\ttry\r\n\t{\r\nif   
(fso.FileExists(strWizTempFile))\r\nreturn true;\r\n";  
  
nLine =  OffsetToLineNumber(strString, 60);  
  
// The return value for the above is 5, because character 60 in the string   
// occurs in the 5th line within the string.  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [LineBeginsWith](../ide/linebeginswith.md)