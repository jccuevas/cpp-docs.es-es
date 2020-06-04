---
title: Error del compilador C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 4eb50ddac51ea78ab3a28d7703384f02eb026ecb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743931"
---
# <a name="compiler-error-c2462"></a>Error del compilador C2462

' Identifier ': no se puede definir un tipo en una expresión ' New-Expression '

No se puede definir un tipo en el campo de operando del operador `new`. Coloque la definición de tipo en una instrucción independiente.

En el ejemplo siguiente se genera C2462:

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
