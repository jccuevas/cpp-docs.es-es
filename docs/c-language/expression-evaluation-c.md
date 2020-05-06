---
title: Evaluación de expresiones (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233852"
---
# <a name="expression-evaluation-c"></a>Evaluación de expresiones (C)

Las expresiones que implican asignación, incremento unario, decremento unario o llamadas a una función pueden tener consecuencias derivadas en su evaluación (efectos secundarios). Cuando se alcanza un "punto de secuencia", todo lo que precede al punto de secuencia, incluidos los efectos secundarios, tiene la garantía de que se ha evaluado antes de que la evaluación empiece en otra parte siguiente al punto de secuencia.

Los "efectos secundarios" son cambios producidos por la evaluación de una expresión. Los efectos secundarios se producen siempre una evaluación de expresiones modifica el valor de una variable. Todas las operaciones de asignación tienen efectos secundarios. Las llamadas de función también pueden tener efectos secundarios si cambian el valor de un elemento visible externamente, ya sea por la asignación directa o por la asignación indirecta a través de un puntero.

## <a name="see-also"></a>Vea también

[Operandos y expresiones](../c-language/operands-and-expressions.md)
