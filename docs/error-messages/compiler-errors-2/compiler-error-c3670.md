---
title: Error del compilador C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: 1b52f58f47027d88d9b0e150ebd2bf4588161553
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758130"
---
# <a name="compiler-error-c3670"></a>Error del compilador C3670

' override ': no se puede invalidar el método de clase base inaccesible ' Method '

Una invalidación solo puede tener lugar en una función cuyo nivel de acceso hace que esté disponible en un tipo derivado. Para obtener más información, vea [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

En el ejemplo siguiente se genera C3670:

```cpp
// C3670.cpp
// compile with: /clr /c
public ref class C {
// Uncomment the following line to resolve.
// public:
   virtual void g() { }
};

public ref class D : public C {
public:
   virtual void f() new sealed = C::g {};   // C3670
};
```
