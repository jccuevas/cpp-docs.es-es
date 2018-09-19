---
title: Efectos secundarios | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6edd636ddb4f59ea0df32846869afc5400edb6dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020113"
---
# <a name="side-effects"></a>Efectos secundarios

El orden de evaluación de expresiones está definido por la implementación concreta, excepto cuando el lenguaje garantiza un orden concreto de evaluación (como se indica en [Prioridad y orden de evaluación](../c-language/precedence-and-order-of-evaluation.md)). Por ejemplo, en las siguientes llamadas de función se producen efectos secundarios:

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

Los argumentos de una llamada de función se pueden evaluar en cualquier orden. Puede que la expresión `i + 1` se evalúe antes que `i = j + 2` o que `i = j + 2` se evalúe antes que `i + 1`. En función de la elección, el resultado es diferente. De igual manera, no es posible garantizar qué caracteres se pasan realmente a `myproc`. Dado que las operaciones de incremento y decremento unario implican asignaciones, tales operaciones pueden producir efectos secundarios, tal y como se muestra en el ejemplo siguiente:

```
x[i] = i++;
```

En este ejemplo, el valor de `x` que se modifica es imprevisible. El valor del subíndice podría ser el valor nuevo o antiguo de `i`. El resultado puede variar según los distintos compiladores o los diferentes niveles de optimización.

Dado que C no define el orden de evaluación de efectos secundarios, los dos métodos de evaluación descritos anteriormente son correctos y se puede implementar cualquiera de ellos. Para asegurarse de que el código sea portátil y claro, evite las instrucciones que dependan de un orden de evaluación concreto para los efectos secundarios.

## <a name="see-also"></a>Vea también

[Evaluación de expresiones](../c-language/expression-evaluation-c.md)