---
title: "GetRuntimeErrorDesc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetRuntimeErrorDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConversionError (método)"
  - "GetRuntimeErrorDesc (método)"
  - "RangeError (método)"
  - "ReferenceError (método)"
  - "RegExpError (método)"
  - "SyntaxError (método)"
  - "TypeError (método)"
  - "URIError (método)"
ms.assetid: d56fdd2e-6ad0-4c49-9e98-bcf0105e1b12
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetRuntimeErrorDesc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve una descripción del tipo de excepción.  
  
## Sintaxis  
  
```  
  
      function GetRuntimeErrorDesc(   
   strRuntimeErrorName    
);  
```  
  
#### Parámetros  
 *strRuntimeErrorName*  
 Nombre del tipo de excepción que se ha producido.  
  
## Valor devuelto  
 Descripción del tipo de excepción.  
  
## Comentarios  
 Devuelve una descripción del tipo de excepción.  Puede ser una de las siguientes excepciones:  
  
|Tipos de excepción|Descripción|  
|------------------------|-----------------|  
|ConversionError|Se produce cuando se intenta convertir un objeto en algo en lo que no se puede convertir.|  
|RangeError|Se produce cuando se proporciona una función con un argumento cuyo intervalo es superior a lo permitido.  Por ejemplo, este error se produce si se intenta crear un objeto `Array` con una longitud que no sea un entero positivo válido.|  
|ReferenceError|Se produce cuando se ha detectado una referencia no válida.  Por ejemplo, este error se producirá si una referencia que se espera es null.|  
|RegExpError|Se produce cuando tiene lugar un error de compilación con una expresión regular.  Una vez compilada la expresión regular, este error no podrá producirse de nuevo.  Por ejemplo, este error se producirá si una expresión regular se declara con un modelo cuya sintaxis no sea válida, o si los marcadores son distintos de *i*, *g* o *m*, o si contiene el mismo marcador más de una vez.|  
|SyntaxError|Se produce cuando, tras analizar el texto de origen, se descubre que su sintaxis no es correcta.  Por ejemplo, este error se producirá si se llama a la función `eval` con un argumento que no sea un texto de programa válido.|  
|TypeError|Se produce cuando el tipo real de un operando no coincide con el tipo esperado.  Un ejemplo de este error consiste en una llamada a una función realizada sobre algo que no es un objeto o que no admite la llamada.|  
|URIError|Se produce cuando se detecta un indicador de recursos uniforme \(URI\) que no es válido.  Por ejemplo, este error se producirá si se encuentra un carácter no válido en una cadena que se va a codificar o descodificar.|  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)