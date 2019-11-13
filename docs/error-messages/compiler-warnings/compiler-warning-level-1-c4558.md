---
title: ADVERTENCIA del compilador (nivel 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: d47e2a619cb84838144b3be6fd45d1f79ecc8661
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966001"
---
# <a name="compiler-warning-level-1-c4558"></a>ADVERTENCIA del compilador (nivel 1) C4558

el valor del operando ' valor ' está fuera del intervalo ' límite inferior-superior '

El valor que se pasa a una instrucción del lenguaje de ensamblado está fuera del intervalo especificado para el parámetro. El valor se truncará.

En el ejemplo siguiente se genera C4558:

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```