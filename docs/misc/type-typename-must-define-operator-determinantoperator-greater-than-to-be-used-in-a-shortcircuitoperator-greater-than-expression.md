---
title: "El tipo &#39;&lt;nombreTipo&gt;&#39; debe definir el operador &#39;&lt;operadorDeterminante&gt;&#39; que se debe usar en una expresi&#243;n &#39;&lt;operadorCortocircuito&gt;&#39; | Microsoft Docs"
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
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreTipo&gt;&#39; debe definir el operador &#39;&lt;operadorDeterminante&gt;&#39; que se debe usar en una expresi&#243;n &#39;&lt;operadorCortocircuito&gt;&#39;
Un [AndAlso \(Operador\)](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) o un [OrElse \(Operador\)](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) usa operandos de un tipo de clase o estructura, cuando esa clase o estructura no define un operador necesario.  
  
 Dado que no se define un operador de cortocircuito \(`AndAlso` o `OrElse`\) directamente, debe definir los operadores lógicos y determinantes correspondientes. En la siguiente tabla se muestran los operadores necesarios.  
  
|Operador de cortocircuito|Operador lógico|Operador determinante|  
|-------------------------------|---------------------|---------------------------|  
|`AndAlso`|[And \(Operador\)](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse \(Operador\)](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or \(Operador\)](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue \(Operador\)](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] usa estos operadores lógicos y determinantes para construir la lógica de cortocircuito para `AndAlso` o `OrElse`. Para que funcione correctamente, ambos operandos y el valor devuelto de la definición de `And` o `Or` deben ser del tipo contenedor, es decir, el tipo de la clase o estructura en la que está definiendo `And` o `Or`.  
  
 **Identificador de error:** BC33035  
  
### Para corregir este error  
  
-   Defina los operadores `And` y `IsFalse`, o los operadores `Or` y `IsTrue` en la clase o estructura que se usa para el tipo de operando del operador `AndAlso` o `OrElse`. Asegúrese de que los operandos para `And` o `Or` son del tipo de la clase o estructura en la que se define.  
  
## Vea también  
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator \(Instrucción\)](../Topic/Operator%20Statement.md)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores lógicos y bit a bit en Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)