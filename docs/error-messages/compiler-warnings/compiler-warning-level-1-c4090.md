---
title: Compilador advertencia (nivel 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462379"
---
# <a name="compiler-warning-level-1-c4090"></a>Compilador advertencia (nivel 1) C4090

'operación': calificadores 'modificador' diferentes

Se define una variable usada en una operación con un modificador especificado que impide que se modifiquen sin ser detectado por el compilador. La expresión se compila sin modificaciones.

Esta advertencia puede deberse a un puntero a un **const** o `volatile` elemento se asigna a un puntero no declarado como puntero a **const** o `volatile`.

Esta advertencia se emite para programas de C. En un programa de C++, el compilador emite un error: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

El ejemplo siguiente genera C4090:

```
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```