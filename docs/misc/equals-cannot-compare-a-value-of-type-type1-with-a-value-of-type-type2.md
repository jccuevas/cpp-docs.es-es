---
title: "&#39;Equals&#39; no puede comparar un valor de tipo &lt;tipo1&gt; con un valor de tipo &lt;tipo2&gt;. | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; no puede comparar un valor de tipo &lt;tipo1&gt; con un valor de tipo &lt;tipo2&gt;.
Un operador `Equals` en una cláusula `Join` o `Group Join` intentó comparar un tipo de datos con otro de una manera no definida. Un ejemplo de esto es una comparación de un valor `Boolean` con un tipo `Date`.  
  
 **Identificador de error:** BC36621  
  
### Para corregir este error  
  
-   Asegúrese de que los valores de cada lado del operador `Equals` se pueden convertir a un tipo de datos común. Algunas opciones para lograrlo son:  
  
    -   Usar la función `CType` para convertir uno o varios de los valores a un tipo específico.  
  
    -   Usar los métodos de conversión o clase <xref:System.Convert> para convertir uno o varios de los valores a un tipo inmutable común.  
  
    -   Convertir los valores en cadenas mediante el método `ToString`.  
  
## Vea también  
 [CType \(Función\)](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [Conversiones de tipos en Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)   
 [Join \(Cláusula\)](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join \(Cláusula\)](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introducción a LINQ en Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)