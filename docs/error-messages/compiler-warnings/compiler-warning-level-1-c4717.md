---
title: Advertencia del compilador (nivel 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0cf9aef8f68ca5972fd3d7886cd8061b88d043ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442567"
---
# <a name="compiler-warning-level-1-c4717"></a>Advertencia del compilador (nivel 1) C4717

'function': recursiva en todas las rutas de control, función provocará el desbordamiento de pila en tiempo de ejecución

Cada ruta de acceso a través de una función contiene una llamada a la función. Dado que no hay ninguna manera de salir de la función sin llamar primero a sí mismo de forma recursiva, la función nunca se cerrará.

El ejemplo siguiente genera C4717:

```
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```