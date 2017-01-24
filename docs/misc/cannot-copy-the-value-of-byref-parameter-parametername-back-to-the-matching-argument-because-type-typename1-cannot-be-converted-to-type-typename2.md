---
title: "No se puede volver a copiar el valor &#39;&lt;parametername&gt;&#39; del par&#225;metro &#39;ByRef&#39; en el argumento correspondiente porque el tipo &#39;&lt;typename1&gt;&#39; no se puede convertir al tipo &#39;&lt;typename2&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33037"
  - "BC33037"
helpviewer_keywords: 
  - "BC33037"
ms.assetid: 3ff137e2-e062-4e54-abf5-e902e2d18968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede volver a copiar el valor &#39;&lt;parametername&gt;&#39; del par&#225;metro &#39;ByRef&#39; en el argumento correspondiente porque el tipo &#39;&lt;typename1&gt;&#39; no se puede convertir al tipo &#39;&lt;typename2&gt;&#39;.
Se declara un procedimiento con un tipo de parámetro que no se puede convertir al tipo de argumento que realiza la llamada.  
  
 Al definir una clase o estructura, puede definir uno o varios operadores de conversión para convertir ese tipo de clase o estructura a otros tipos. También puede definir operadores de conversión inversos para convertir esos otros tipos de nuevo a su clase o tipo de estructura. Cuando use su tipo de clase o estructura en una llamada de procedimiento, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] puede usar estos operadores de conversión para convertir el tipo de un argumento al tipo del parámetro correspondiente.  
  
 Si pasa el argumento [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md), [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] a veces copia el valor del argumento en una variable local en el procedimiento en lugar de pasar una referencia. En tal caso, cuando el procedimiento vuelve, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] debe copiar el valor de la variable local de nuevo en el argumento en el código de llamada.  
  
 Si un valor de argumento `ByRef` se copia en el procedimiento y el argumento y el parámetro son del mismo tipo, no es necesario realizar ninguna conversión. Pero si los tipos son diferentes, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] se debe convertir en ambas direcciones. Si uno de los tipos es su tipo de clase o estructura, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] lo debe convertir a y desde el otro tipo. Esto significa que debe definir operadores de conversión en ambas direcciones.  
  
 **Identificador de error:** BC33037  
  
### Para corregir este error  
  
-   Si es posible, use un argumento de llamada del mismo tipo, como el parámetro de procedimiento, por lo que [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] no necesita hacer ninguna conversión.  
  
-   Si necesita llamar al procedimiento con un argumento de tipo diferente del tipo de parámetro pero no es necesario devolver un valor al argumento de llamada, defina el parámetro para que sea [ByVal](../Topic/ByVal%20\(Visual%20Basic\).md) en lugar de `ByRef`.  
  
-   Si necesita devolver un valor al argumento de llamada, defina el operador de conversión inversa para que [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] se pueda volver a convertir al tipo de argumento que realiza la llamada.  
  
## Vea también  
 [Procedimientos](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [Argumentos y parámetros de procedimiento](../Topic/Procedure%20Parameters%20and%20Arguments%20\(Visual%20Basic\).md)   
 [Pasar argumentos por valor y por referencia](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator \(Instrucción\)](../Topic/Operator%20Statement.md)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)