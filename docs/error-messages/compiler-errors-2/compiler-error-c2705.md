---
title: Error del compilador C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616276"
---
# <a name="compiler-error-c2705"></a>Error del compilador C2705

'label': salto no válido en el ámbito del 'bloque del controlador de excepciones'

La ejecución salta a una etiqueta dentro de un `try` / `catch`, `__try` / `__except`, `__try` / `__finally` bloque. Para más información, consulte [Control de excepciones](../../cpp/exception-handling-in-visual-cpp.md).

El ejemplo siguiente genera C2705:

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```