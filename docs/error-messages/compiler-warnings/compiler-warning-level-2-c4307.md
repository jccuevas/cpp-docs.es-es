---
title: ADVERTENCIA del compilador (nivel 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052068"
---
# <a name="compiler-warning-level-2-c4307"></a>ADVERTENCIA del compilador (nivel 2) C4307

' Operator ': desbordamiento constante integral

El operador se usa en una expresión que da como resultado una constante de tipo entero que desborda el espacio asignado para él. Es posible que tenga que usar un tipo mayor para la constante. Un entero **con signo** contiene un valor menor que un `unsigned int` porque el entero **con signo** usa un bit para representar el signo.

En el ejemplo siguiente se genera C4307:

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```