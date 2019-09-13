---
title: Advertencia del compilador (nivel 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 2d5ae8fcf5a527031c3a974b227f713675f31ffa
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926099"
---
# <a name="compiler-warning-level-1-c4319"></a>Advertencia del compilador (nivel 1) C4319

> ' ~ ': extensión de cero de '*tipo1*' a '*tipo2*' de mayor tamaño

El resultado del **~** operador (complemento bit a bit) es sin signo y después se extiende a cero cuando se convierte en un tipo mayor.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo, `~(a - 1)` se evalúa como una expresión larga sin signo de 32 bits y, a continuación, se convierte a 64 bits por extensión cero. Esto podría producir resultados de operación inesperados.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
