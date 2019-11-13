---
title: ADVERTENCIA del compilador (nivel 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 182f9ff061fd2a8ebe5ea0046545412fca5f646a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965587"
---
# <a name="compiler-warning-level-1-c4405"></a>ADVERTENCIA del compilador (nivel 1) C4405

' Identifier ': el identificador es una palabra reservada

Una palabra reservada para el ensamblado alineado se usa como un nombre de variable. Esto puede producir resultados imprevisibles. Para corregir esta advertencia, evite asignar nombres a las variables con palabras reservadas para el ensamblado alineado. En el ejemplo siguiente se genera C4405:

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```