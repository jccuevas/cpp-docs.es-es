---
title: Advertencia del compilador (nivel 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: dd1db3cccf9f1b24f82ddddf10fcf35f39a9251a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988791"
---
# <a name="compiler-warning-level-4-c4932"></a>Advertencia del compilador (nivel 4) C4932

__identifier (identifier) y \__identifier (identifier) no se pueden distinguir

El compilador es no puede distinguir entre **_finally** y `__finally` o entre `__try` y **_try** como parámetro pasado a [__identifier](../../extensions/identifier-cpp-cli.md). No debería intentar usar ambos como identificadores en el mismo programa, ya que provocarán un error [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

El ejemplo siguiente genera la advertencia C4932:

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
