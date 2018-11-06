---
title: Error del compilador C3654
ms.date: 11/04/2016
f1_keywords:
- C3654
helpviewer_keywords:
- C3654
ms.assetid: 57d96e3f-6bbb-4eaa-934b-26c23b4ceb2e
ms.openlocfilehash: eca5081daaaf92a7b95a076a1e93bc06799bd9f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649025"
---
# <a name="compiler-error-c3654"></a>Error del compilador C3654

'texto': error de sintaxis en la invalidación explícita

Era una cadena inesperada en un reemplazo explícito. Para obtener más información, consulte [invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md).

El ejemplo siguiente genera C3654:

```
// C3654.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f() = 0;
   virtual void g() = 0;
   virtual void h() = 0;
};

public ref struct Q : B {
   virtual void f() = B::f, 3 {}   // C3654
   // try the following line instead
   // virtual void g() = B::g, B::h {}
};
```