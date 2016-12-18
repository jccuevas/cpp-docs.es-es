---
title: "El operando &#39;IsNot&#39; del tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; &#250;nicamente se puede comparar con &#39;Nothing&#39; porque &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; es un par&#225;metro de tipo sin restricci&#243;n de clase | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando &#39;IsNot&#39; del tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; &#250;nicamente se puede comparar con &#39;Nothing&#39; porque &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; es un par&#225;metro de tipo sin restricci&#243;n de clase
Se usa un parámetro de tipo como operando para [IsNot \(Operador\)](../Topic/IsNot%20Operator%20\(Visual%20Basic\).md) cuando el parámetro de tipo está definido sin la palabra clave [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) o un nombre de clase específico en su lista de restricciones.  
  
 `IsNot` compara dos tipos de referencia para determinar si señalan a distintas instancias de objeto en memoria. No puede tomar un operando que no es un tipo de referencia, a menos que el otro operando sea [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md).  
  
 **Identificador de error:** BC32097  
  
### Para corregir este error  
  
-   Si puede requerir que el argumento de tipo proporcionado para este parámetro de tipo siempre sea un tipo de referencia, agregue la palabra clave `Class` o un nombre de clase específico a la lista de restricciones del parámetro de tipo.  
  
-   Si no se requiere que el argumento de tipo proporcionado a este parámetro de tipo siempre sea un tipo de referencia, quítelo de la expresión `IsNot`. No se puede comparar con otros tipos de referencia con el operador `IsNot`.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Lista de tipos](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Tipos de valor y tipos de referencia](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [Operadores de comparación en Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)