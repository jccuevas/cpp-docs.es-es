---
title: Error del compilador C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: f5799511575617ad1705bbce50a939ee46599628
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755348"
---
# <a name="compiler-error-c3285"></a>Error del compilador C3285

la instrucción for each no puede utilizarse en variables de tipo 'type'

La instrucción `for each` repite un grupo de instrucciones incrustadas por cada elemento de una matriz o una colección de objetos.

Vea [for each, in](../../dotnet/for-each-in.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3285.

```cpp
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```
