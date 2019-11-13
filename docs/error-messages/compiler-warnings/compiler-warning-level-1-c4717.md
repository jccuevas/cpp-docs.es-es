---
title: ADVERTENCIA del compilador (nivel 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0bc95cc770914a1c02a7a40f9754415c2f013d63
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051345"
---
# <a name="compiler-warning-level-1-c4717"></a>ADVERTENCIA del compilador (nivel 1) C4717

' función ': recursivo en todas las rutas de acceso de control. la función causará el desbordamiento de la pila en tiempo de ejecución

Cada ruta de acceso a través de una función contiene una llamada a la función. Dado que no hay ninguna manera de salir de la función sin llamarlo a sí mismo de forma recursiva, la función nunca se cerrará.

En el ejemplo siguiente se genera C4717:

```cpp
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