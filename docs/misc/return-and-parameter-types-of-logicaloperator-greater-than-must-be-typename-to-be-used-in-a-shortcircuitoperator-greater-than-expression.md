---
title: "Los tipos de valor devueltos y de par&#225;metro de &#39;&lt;operadorL&#243;gico&gt;&#39; deben ser &#39;&lt;nombreTipo&gt;&#39; para usarse en una expresi&#243;n &#39;&lt;operadorCortocircuito&gt;&#39; | Microsoft Docs"
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
  - "vbc33034"
  - "bc33034"
helpviewer_keywords: 
  - "BC33034"
ms.assetid: 94cd52dc-5d48-4673-b0b8-38a1954483c6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de valor devueltos y de par&#225;metro de &#39;&lt;operadorL&#243;gico&gt;&#39; deben ser &#39;&lt;nombreTipo&gt;&#39; para usarse en una expresi&#243;n &#39;&lt;operadorCortocircuito&gt;&#39;
Un operador `And` o un operador `Or` se declara con un tipo de valor devuelto o parámetros no adecuados para su uso en un [AndAlso \(Operador\)](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) o un [OrElse \(Operador\)](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md).  
  
 Dado que no se define un operador de cortocircuito \(`AndAlso` o `OrElse`\) directamente, debe definir los operadores lógicos y determinantes correspondientes. En la siguiente tabla se muestran los operadores necesarios.  
  
|Operador de cortocircuito|Operador lógico|Operador determinante|  
|-------------------------------|---------------------|---------------------------|  
|`AndAlso`|[And \(Operador\)](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse \(Operador\)](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or \(Operador\)](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue \(Operador\)](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] usa estos operadores lógicos y determinantes para construir la lógica de cortocircuito para `AndAlso` o `OrElse`. Para que funcione correctamente, ambos operandos y el valor devuelto de la definición de `And` o `Or` deben ser del tipo contenedor, es decir, el tipo de la clase o estructura en la que está definiendo `And` o `Or`.  
  
 **Identificador de error:** BC33034  
  
### Para corregir este error  
  
-   Cambie el tipo de los operandos y el valor devuelto al tipo de la clase o estructura en la que define este operador.  
  
     O bien  
  
-   No use el operador de cortocircuito correspondiente \(`AndAlso` o `OrElse`\) con operandos del tipo de la clase o estructura en la que define este operador `And` o `Or`.  
  
## Vea también  
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator \(Instrucción\)](../Topic/Operator%20Statement.md)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores lógicos y bit a bit en Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)