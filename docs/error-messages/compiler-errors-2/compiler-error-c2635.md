---
title: Error del compilador C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 90bc30460cb578d1ed2812e40907a361eeb3b039
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748429"
---
# <a name="compiler-error-c2635"></a>Error del compilador C2635

no se puede convertir un ' identificador1 * ' en ' identificador2\*'; la conversión de una clase base virtual es implícita

La conversión requiere una conversión de una clase base `virtual` a una clase derivada, lo cual no está permitido.

En el ejemplo siguiente se genera C2635:

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
