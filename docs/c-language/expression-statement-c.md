---
title: Expression (Instrucción) (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: b825e88703e1913d9b6d916360174060854c632a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667472"
---
# <a name="expression-statement-c"></a>Expression (Instrucción) (C)

Cuando se ejecuta una instrucción de expresión, la expresión se evalúa según las reglas descritas en [Expresiones y asignaciones](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Sintaxis

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

Todos los efectos secundarios de la evaluación de la expresión se completan antes de que se ejecute la instrucción siguiente. Una instrucción de expresión vacía se conoce como instrucción nula. Para obtener más información, vea [La instrucción Null](../c-language/null-statement-c.md).

En estos ejemplos se muestran instrucciones de expresión.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

En la última instrucción, la expresión de llamada de función, el valor de la expresión, que incluye cualquier valor devuelto por la función, se incrementa en 3 y, a continuación, se asigna a las variables `y` y `z`.

## <a name="see-also"></a>Vea también

[Instrucciones](../c-language/statements-c.md)