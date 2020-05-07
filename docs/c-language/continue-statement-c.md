---
title: continue (Instrucción) (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 983775e6fe9887afa5784358ede1de9583b3afba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312568"
---
# <a name="continue-statement-c"></a>continue (Instrucción) (C)

La instrucción `continue` pasa el control a la siguiente iteración de la instrucción de inclusión `do`, `for` o `while` más próxima en que aparece, omitiendo las restantes instrucciones en el cuerpo de la instrucción `do`, `for` o `while`.

## <a name="syntax"></a>Sintaxis

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**continue ;**

La siguiente iteración de una instrucción `do`, de `for` o `while` se determina de la manera siguiente:

- Dentro de una instrucción `do` o `while`, la siguiente iteración empieza evaluando de nuevo la expresión de la instrucción `do` o `while`.

- Una instrucción `continue` en una instrucción `for` hace que se evalúe la expresión de bucle de la instrucción `for`. A continuación, el compilador evalúa de nuevo la expresión condicional y, dependiendo del resultado, finaliza o recorre en iteración el cuerpo de la instrucción. Vea [La instrucción for](../c-language/for-statement-c.md) para obtener más información sobre la instrucción `for` y sus elementos no terminales.

Este es un ejemplo de la instrucción `continue`:

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

En este ejemplo, se ejecuta el cuerpo de la instrucción mientras `i` sea mayor que 0. En primer lugar, `f(i)` se asigna a `x`; a continuación, si `x` es igual a 1, se ejecuta la instrucción `continue`. El resto de las instrucciones del cuerpo se omite, y la ejecución se reanuda en la parte superior del bucle con la evaluación de la prueba del bucle.

## <a name="see-also"></a>Vea también

[continue (Instrucción)](../cpp/continue-statement-cpp.md)
