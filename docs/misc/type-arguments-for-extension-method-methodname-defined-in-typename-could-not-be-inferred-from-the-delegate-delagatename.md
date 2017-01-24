---
title: "Los argumentos de tipo para el m&#233;todo de extensi&#243;n &#39;&lt;nombreDeM&#233;todo&gt;&#39; definido en &#39;&lt;nombreDeTipo&gt;&#39; no se pudieron inferir a partir del delegado &#39;&lt;nombreDeDelegado&gt;&#39; | Microsoft Docs"
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
  - "bc36581"
  - "vbc36581"
helpviewer_keywords: 
  - "BC36581"
ms.assetid: 2bb9ca8d-7293-40e9-9285-e20b8254b3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los argumentos de tipo para el m&#233;todo de extensi&#243;n &#39;&lt;nombreDeM&#233;todo&gt;&#39; definido en &#39;&lt;nombreDeTipo&gt;&#39; no se pudieron inferir a partir del delegado &#39;&lt;nombreDeDelegado&gt;&#39;
Una instrucción de asignación usa `AddressOf` para asignar la dirección de una extensión genérica un método de extensión genérico a un delegado, pero no proporciona ningún argumento de tipo al método de extensión.  
  
 Normalmente, cuando se invoca un método genérico, se facilita un argumento de tipo para cada parámetro de tipo que define el método genérico. Si no se facilita ningún argumento de tipo, el compilador intenta inferir los tipos que se deben pasar a los parámetros de tipo. Si el contexto no proporciona suficiente información para que el compilador infiera los tipos, se genera un error.  
  
 **Identificador de error:** BC36581  
  
### Para corregir este error  
  
-   En la expresión `AddressOf`, especifique los argumentos de tipo para el método de extensión.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf \(Operador\)](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Procedimientos genéricos en Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Lista de tipos](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [métodos de extensión.](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)