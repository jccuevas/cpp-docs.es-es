---
title: Advertencia del compilador (nivel 1) C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: 1fb2dc7fd4bc685e457898b47c513c21009146ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585554"
---
# <a name="compiler-warning-level-1-c4552"></a>Advertencia del compilador (nivel 1) C4552

'operador': operador no tiene ningún efecto; se esperaba un operador con efectos secundarios

Si una instrucción de expresión tiene un operador con ningún efecto secundario como la parte superior de la expresión, probablemente es un error.

Para invalidar esta advertencia, coloque la expresión entre paréntesis.

El ejemplo siguiente genera C4552:

```
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```