---
title: "Debe hacer referencia al menos a una variable de rango en ambos lados del operador &#39;Equals&#39;. | Microsoft Docs"
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
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Debe hacer referencia al menos a una variable de rango en ambos lados del operador &#39;Equals&#39;.
Debe hacer referencia al menos a una variable de rango en ambos lados del operador 'Equals'. Las variables de rango \<variables\> deben aparecer en un lado del operador 'Equals' y las variables de rango \<variables\> deben aparecer en el otro.  
  
 Las variables de rango identificadas para colecciones que se van a combinar en una consulta LINQ deben estar en lados opuestos del operador `Equals`, en función de la colección en la que se han identificado. Es decir, las variables de rango identificadas para una de las colecciones que se están combinando deben estar en el lado opuesto del operador `Equals` de las variables de rango de la otra colección que se está combinando. No se pueden mezclar las variables de rango de colecciones independientes en el mismo lado del operador `Equals`.  
  
 Debe hacerse referencia al menos a una variable de cada colección que se está combinando a cada lado del operador `Equals`.  
  
 **Identificador de error:** BC36622  
  
## Vea también  
 [Introducción a LINQ en Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)   
 [Join \(Cláusula\)](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join \(Cláusula\)](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [From \(Cláusula\)](../Topic/From%20Clause%20\(Visual%20Basic\).md)   
 [Select \(Cláusula\)](../Topic/Select%20Clause%20\(Visual%20Basic\).md)