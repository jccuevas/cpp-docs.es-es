---
title: ADVERTENCIA del compilador (nivel 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: c1721d472c81c62ba01282f43c7e678d7f84206b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200088"
---
# <a name="compiler-warning-level-1-c4142"></a>ADVERTENCIA del compilador (nivel 1) C4142

redefinición benigna de tipo

Un tipo se redefine de forma que no tiene ningún efecto en el código generado.

Posibles causas del error:

- Una función miembro de una clase derivada tiene un tipo de valor devuelto diferente de la función miembro correspondiente de la clase base.

- Un tipo definido con el comando `typedef` se redefine con una sintaxis diferente.

En el ejemplo siguiente se genera C4142:

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
