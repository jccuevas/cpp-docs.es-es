---
title: Expression (Instrucción) (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148795"
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
