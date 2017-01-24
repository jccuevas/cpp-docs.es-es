---
title: "Evaluaci&#243;n de expresiones (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "evaluación de expresiones"
  - "expresiones [C++], evaluar"
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Evaluaci&#243;n de expresiones (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las expresiones que implican asignación, incremento unario, decremento unario o llamadas a una función pueden tener consecuencias derivadas en su evaluación \(efectos secundarios\).  Cuando se alcanza un "punto de secuencia", todo lo que precede al punto de secuencia, incluidos los efectos secundarios, tiene la garantía de que se ha evaluado antes de que la evaluación empiece en otra parte siguiente al punto de secuencia.  
  
 Los "efectos secundarios" son cambios producidos por la evaluación de una expresión.  Los efectos secundarios se producen siempre una evaluación de expresiones modifica el valor de una variable.  Todas las operaciones de asignación tienen efectos secundarios.  Las llamadas de función también pueden tener efectos secundarios si cambian el valor de un elemento visible externamente, ya sea por la asignación directa o por la asignación indirecta a través de un puntero.  
  
## Vea también  
 [Operandos y expresiones](../c-language/operands-and-expressions.md)