---
title: "Los operadores no se pueden declarar &#39;&lt;palabraClave&gt;&#39;. | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores no se pueden declarar &#39;&lt;palabraClave&gt;&#39;.
Un operador está declarado con una palabra clave que no es válida para las definiciones de operador.  
  
 Cada operador debe declararse como [Public](../Topic/Public%20\(Visual%20Basic\).md) y [Shared](../Topic/Shared%20\(Visual%20Basic\).md). Además, un operador de conversión se debe declarar con [Widening](../Topic/Widening%20\(Visual%20Basic\).md) o [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md), pero no con ambos. Una definición de operador puede incluir opcionalmente las palabras clave [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) y [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md). No se permiten otras palabras clave en una [Operator \(Instrucción\)](../Topic/Operator%20Statement.md).  
  
 **Identificador de error:** BC33013  
  
### Para corregir este error  
  
-   Quite la palabra clave no válida de la definición de operador.  
  
## Vea también  
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)