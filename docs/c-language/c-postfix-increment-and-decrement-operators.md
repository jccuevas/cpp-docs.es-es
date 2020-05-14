---
title: Operadores de incremento y decremento postfijos de C
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8c2e3ba50ce3e768b377a588cd3e82ad29df79ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325580"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operadores de incremento y decremento postfijos de C

Los operandos de los operadores de incremento y decremento de postfijo son tipos escalares que son valores L modificables.

## <a name="syntax"></a>Sintaxis

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

El resultado de la operación de incremento y decremento de postfijo es el valor del operando. Una vez obtenido el resultado, se incrementa (o se reduce) el valor del operando. En el código siguiente se muestra el operador de incremento de postfijo.

```
if( var++ > 0 )
    *p++ = *q++;
```

En este ejemplo, la variable `var` se compara con 0 y luego se incrementa. Si `var` era positivo antes de que se incrementara, se ejecuta la siguiente instrucción. En primer lugar, se asigna el valor del objeto indicado por `q` al objeto indicado por `p`. A continuación, se incrementan `q` y `p`.

## <a name="see-also"></a>Vea también

[Operadores de incremento y decremento postfijos: ++ y --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
