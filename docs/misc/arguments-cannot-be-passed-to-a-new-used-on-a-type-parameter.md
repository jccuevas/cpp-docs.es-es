---
title: "No se pueden pasar argumentos a &#39;New&#39; si se usan en un par&#225;metro de tipo. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden pasar argumentos a &#39;New&#39; si se usan en un par&#225;metro de tipo.
Una instrucción de declaración o de asignación invoca un tipo genérico y proporciona argumentos de constructor a un parámetro de tipo que tiene la restricción [New \(Operador\)](../Topic/New%20Operator%20\(Visual%20Basic\).md).  
  
 Una lista de restricciones en un parámetro de tipo puede especificar que el argumento de tipo pasado a ese parámetro de tipo debe exponer un constructor sin parámetros que pueda tener acceso al código de creación. Un parámetro de tipo no puede requerir un constructor que toma parámetros y un parámetro de tipo con la restricción `New` no puede aceptar este tipo de constructor.  
  
 **Identificador de error:** BC32085  
  
### Para corregir este error  
  
-   Quite la lista de argumentos del siguiente argumento de tipo de la instrucción que invoca el tipo genérico. No se pueden pasar argumentos de constructor al parámetro de tipo correspondiente.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Tipos de valor y tipos de referencia](../Topic/Value%20Types%20and%20Reference%20Types.md)