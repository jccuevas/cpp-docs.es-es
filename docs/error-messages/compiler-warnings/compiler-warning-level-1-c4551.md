---
title: ADVERTENCIA del compilador (nivel 1) C4551
ms.date: 11/04/2016
f1_keywords:
- C4551
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
ms.openlocfilehash: d4e7467efa8308e1044e8b7a166174c173dab166
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966364"
---
# <a name="compiler-warning-level-1-c4551"></a>ADVERTENCIA del compilador (nivel 1) C4551

falta la lista de argumentos de la llamada de función

Una llamada de función debe incluir los paréntesis de apertura y cierre después del nombre de la función, incluso si la función no toma ningún parámetro.

En el ejemplo siguiente se genera C4551:

```cpp
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```