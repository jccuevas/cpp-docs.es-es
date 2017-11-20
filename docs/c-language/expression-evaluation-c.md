---
title: "Evaluación de expresiones (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21b78b659b4d4cd8f3bb5db849b3c64a5f66f971
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluation-c"></a>Evaluación de expresiones (C)
Las expresiones que implican asignación, incremento unario, decremento unario o llamadas a una función pueden tener consecuencias derivadas en su evaluación (efectos secundarios). Cuando se alcanza un "punto de secuencia", todo lo que precede al punto de secuencia, incluidos los efectos secundarios, tiene la garantía de que se ha evaluado antes de que la evaluación empiece en otra parte siguiente al punto de secuencia.  
  
 Los "efectos secundarios" son cambios producidos por la evaluación de una expresión. Los efectos secundarios se producen siempre una evaluación de expresiones modifica el valor de una variable. Todas las operaciones de asignación tienen efectos secundarios. Las llamadas de función también pueden tener efectos secundarios si cambian el valor de un elemento visible externamente, ya sea por la asignación directa o por la asignación indirecta a través de un puntero.  
  
## <a name="see-also"></a>Vea también  
 [Operandos y expresiones](../c-language/operands-and-expressions.md)