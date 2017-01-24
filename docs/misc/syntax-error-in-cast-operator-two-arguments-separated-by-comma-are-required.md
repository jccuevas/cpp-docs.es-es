---
title: "Error de sintaxis en el operador de conversi&#243;n; se necesitan dos argumentos separados por coma | Microsoft Docs"
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
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de sintaxis en el operador de conversi&#243;n; se necesitan dos argumentos separados por coma
Una expresión usa la función de conversión `CType` o la palabra clave de conversión `DirectCast` o `TryCast`, pero solo proporciona un argumento.  
  
 `CType`, `DirectCast` y `TryCast` requieren dos argumentos. El primero es una expresión que se va a convertir y el segundo es el tipo de datos o el tipo de clase al que se va a convertir.  
  
 **Identificador de error:** BC30944  
  
### Para corregir este error  
  
-   Proporcione los dos argumentos según sea necesario para la conversión.  
  
-   Si tiene previsto usar una de las [Funciones de conversión de tipos](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md) específicas como `CString`, debe usar ese nombre de función en lugar de `CType`. En ese caso, se necesita un único argumento.  
  
## Vea también  
 [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast \(Operador\)](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast \(Operador\)](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Funciones de conversión de tipos](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)