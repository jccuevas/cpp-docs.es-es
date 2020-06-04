---
title: Error del compilador C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: f8d67ac0ff6a1fa5d9efbb8d85747ff94d75c648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742501"
---
# <a name="compiler-error-c3638"></a>Error del compilador C3638

' Operator ': los operadores de conversión boxing y unboxing estándar no se pueden redefinir

El compilador define un operador de conversión para que cada clase administrada admita la conversión boxing implícita. Este operador no se puede redefinir.

Para obtener más información, vea [conversión boxing implícita](../../extensions/boxing-cpp-component-extensions.md).

En el ejemplo siguiente se genera C3638:

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
