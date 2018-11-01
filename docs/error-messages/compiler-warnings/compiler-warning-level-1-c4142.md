---
title: Compilador advertencia (nivel 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456087"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilador advertencia (nivel 1) C4142

¡¡¡Redefinición benigno de tipo

Se vuelve a definir un tipo de forma que no tiene ningún efecto en el código generado.

Posibles causas del error:

- Una función miembro de una clase derivada tiene un tipo de valor devuelto diferente de la función miembro correspondiente de la clase base.

- Un tipo definido con el `typedef` se vuelve a definir comandos con una sintaxis diferente.

El ejemplo siguiente genera C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```