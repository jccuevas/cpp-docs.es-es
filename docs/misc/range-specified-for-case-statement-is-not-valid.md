---
title: "El rango especificado para la instrucci&#243;n &#39;Case&#39; no es v&#225;lido | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El rango especificado para la instrucci&#243;n &#39;Case&#39; no es v&#225;lido
Se ha especificado un intervalo no válido para una instrucción `Case`.  
  
 Cuando se compara la misma expresión con varios valores diferentes, puede utilizar las instrucciones `Select...Case` como una alternativa a las instrucciones `If...Then...Else`. Aunque las instrucciones `If` y `ElseIf` pueden evaluar una expresión diferente en cada instrucción, la instrucción `Select` evalúa una única expresión solo una vez y después la utiliza en cada comparación. Cada instrucción `Case` puede contener más de un valor, un intervalo de valores o una combinación de valores y operadores de comparación.  
  
 **Id. de error:** BC40052  
  
### Para corregir este error  
  
-   Modifique el intervalo para incluir todos los valores o use una instrucción `Case Else` para capturar un valor indefinido.  
  
## Vea también  
 [Select...Case \(Instrucción\)](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [Estructuras de decisión](../Topic/Decision%20Structures%20\(Visual%20Basic\).md)   
 [Conversiones de ampliación y de restricción](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)