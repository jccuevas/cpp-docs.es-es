---
title: "No se pueden aplicar los argumentos de tipo en la expresi&#243;n &#39;&lt;expression&gt;&#39; | Microsoft Docs"
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
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden aplicar los argumentos de tipo en la expresi&#243;n &#39;&lt;expression&gt;&#39;
Un alias de importación se define con una cláusula [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) que pasa argumentos de tipo al alias de importación.  
  
 Se utilizan argumentos de tipo para tipos genéricos y solo las clases, las estructuras, las interfaces, los procedimientos y los delegados pueden ser genéricos. Ni los espacios de nombres ni los alias de importación pueden ser genéricos.  
  
 **Id. de error:** BC32058  
  
### Para corregir este error  
  
-   Quite la cláusula `Of` y sus argumentos de tipo del alias de importación.  
  
## Vea también  
 [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [Referencias y la instrucción Imports](../Topic/References%20and%20the%20Imports%20Statement%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Tipos genéricos en Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Lista de tipos](../Topic/Type%20List%20\(Visual%20Basic\).md)