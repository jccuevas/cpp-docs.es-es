---
title: "No se permite &#39;Group&#39; en este contexto; se esperaba un identificador | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite &#39;Group&#39; en este contexto; se esperaba un identificador
La palabra clave `Group` se incluye en la sección `Into` de un cláusula `Aggregate`. La palabra clave `Group` solo es válido en las cláusulas `Group By` o `Group Join`.  
  
 **Identificador de error:** BC36618  
  
### Para corregir este error  
  
-   Quite la palabra clave `Group` de la cláusula `Aggregate`. Puede agregar una cláusula `Group By` a la consulta para agrupar los resultados.  
  
## Vea también  
 [Aggregate \(Cláusula\)](../Topic/Aggregate%20Clause%20\(Visual%20Basic\).md)   
 [Group By \(Cláusula\)](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join \(Cláusula\)](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introducción a LINQ en Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)