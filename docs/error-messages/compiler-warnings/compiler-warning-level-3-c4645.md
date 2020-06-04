---
title: Advertencia del compilador (nivel 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: d9aff4b554f4b162f87de9e1d373d59dea019637
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991733"
---
# <a name="compiler-warning-level-3-c4645"></a>Advertencia del compilador (nivel 3) C4645

la función declarada con __declspec(noreturn) tiene una instrucción return

A [return](../../cpp/return-statement-in-program-termination-cpp.md) en una función marcada con el modificador [noreturn](../../cpp/noreturn.md) `__declspec` . Se omitió la instrucción `return` .

El ejemplo siguiente genera la advertencia C4645:

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```
