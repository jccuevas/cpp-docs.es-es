---
title: Error del compilador C2875
ms.date: 11/04/2016
f1_keywords:
- C2875
helpviewer_keywords:
- C2875
ms.assetid: d589fc0c-08b2-4a79-bc0e-dca5eb80bdd5
ms.openlocfilehash: cefb2c0b138c0a6a6061e990e6bb79ce9b93f6b5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736339"
---
# <a name="compiler-error-c2875"></a>Error del compilador C2875

la declaración Using genera una declaración múltiple de ' Class:: Identifier '

La declaración hace que el mismo elemento se defina dos veces.

En el ejemplo siguiente se genera C2875:

```cpp
// C2875.cpp
struct A {
   void f(int*);
};

struct B {
   void f(double*);
};

struct AB : A, B {
   using A::f;
   using A::f;   // C2875
   using B::f;
};
```
