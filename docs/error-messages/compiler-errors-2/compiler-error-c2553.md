---
title: Error del compilador C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756791"
---
# <a name="compiler-error-c2553"></a>Error del compilador C2553

' base_function ': el tipo de valor devuelto de la función virtual de invalidación es distinto de ' override_function '

Una función de una clase derivada intentó reemplazar una función virtual en una clase base, pero la función de la clase derivada no tenía el mismo tipo de valor devuelto que la función de clase base.  Una firma de función de invalidación debe coincidir con la firma de la función que se va a invalidar.

En el ejemplo siguiente se genera C2553:

```cpp
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```
