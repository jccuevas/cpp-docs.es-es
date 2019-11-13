---
title: ADVERTENCIA del compilador (nivel 1) C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: b9f7fcd5a1949082aad75407f230db2e32dddd67
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966356"
---
# <a name="compiler-warning-level-1-c4552"></a>ADVERTENCIA del compilador (nivel 1) C4552

' Operator ': el operador no tiene ningún efecto; se esperaba un operador con efectos secundarios

Si una instrucción de expresión tiene un operador sin ningún efecto secundario como parte superior de la expresión, es probable que se trate de un error.

Para invalidar esta advertencia, coloque la expresión entre paréntesis.

En el ejemplo siguiente se genera C4552:

```cpp
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```