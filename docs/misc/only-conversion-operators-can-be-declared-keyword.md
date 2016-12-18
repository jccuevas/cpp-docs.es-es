---
title: "Solo los operadores de conversi&#243;n se pueden declarar como &#39;&lt;palabra clave&gt;&#39;. | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solo los operadores de conversi&#243;n se pueden declarar como &#39;&lt;palabra clave&gt;&#39;.
Una [Operator \(Instrucción\)](../Topic/Operator%20Statement.md) especifica [Widening](../Topic/Widening%20\(Visual%20Basic\).md) o [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) cuando el operador no es un operador de conversión.  
  
 Cada operador debe declararse como [Public](../Topic/Public%20\(Visual%20Basic\).md) y [Shared](../Topic/Shared%20\(Visual%20Basic\).md). Sin embargo, solo se puede declarar un operador de conversión con [Widening](../Topic/Widening%20\(Visual%20Basic\).md) o [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md), pero no ambos.  
  
 Una definición de operador puede incluir opcionalmente las palabras clave [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) y [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md). No hay otras palabras clave permitidas en una [Operator \(Instrucción\)](../Topic/Operator%20Statement.md).  
  
 **Identificador de error:** BC33019  
  
### Para corregir este error  
  
1.  Quite la palabra clave `Widening` o `Narrowing` de la definición del operador. No se aplican porque no se realiza ninguna conversión de tipos.  
  
## Vea también  
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator \(Instrucción\)](../Topic/Operator%20Statement.md)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Conversiones de tipos en Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)