---
title: Advertencia del compilador (nivel 1) C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385477"
---
# <a name="compiler-warning-level-1-c4319"></a>Advertencia del compilador (nivel 1) C4319

> ' ~': extensión de cero '*type1*'para'*type2*' de mayor tamaño

El resultado de la **~** (complemento bit a bit) (operador) es sin signo y, a continuación, completa con ceros cuando se convierte a un tipo mayor.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `~(a - 1)` se evalúa como una expresión de tipo long sin signo de 32 bits y, a continuación, convierte a 64 bits mediante extensión con ceros. Esto podría producir resultados de operación inesperados.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
