---
title: "Evaluación de expresiones (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a24e94fe4a5c89dad40b7253690475d0cc7bd0eb
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="expression-evaluation-c"></a>Evaluación de expresiones (C)
Las expresiones que implican asignación, incremento unario, decremento unario o llamadas a una función pueden tener consecuencias derivadas en su evaluación (efectos secundarios). Cuando se alcanza un "punto de secuencia", todo lo que precede al punto de secuencia, incluidos los efectos secundarios, tiene la garantía de que se ha evaluado antes de que la evaluación empiece en otra parte siguiente al punto de secuencia.  
  
 Los "efectos secundarios" son cambios producidos por la evaluación de una expresión. Los efectos secundarios se producen siempre una evaluación de expresiones modifica el valor de una variable. Todas las operaciones de asignación tienen efectos secundarios. Las llamadas de función también pueden tener efectos secundarios si cambian el valor de un elemento visible externamente, ya sea por la asignación directa o por la asignación indirecta a través de un puntero.  
  
## <a name="see-also"></a>Vea también  
 [Operandos y expresiones](../c-language/operands-and-expressions.md)
