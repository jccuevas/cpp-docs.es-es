---
title: Advertencia del compilador (nivel 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 1583da44368225eabd8181be970f69f6582111e1
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682979"
---
# <a name="compiler-warning-level-4-c4487"></a>Advertencia del compilador (nivel 4) C4487

' derived_class_function ': coincide con el método no virtual heredado ' base_class_function ' pero no se ha marcado explícitamente como ' New '

Una función de una clase derivada tiene la misma firma que una función de clase base no virtual. C4487 recuerda que la función de clase derivada no invalida la función de clase base. Marque explícitamente la función de la clase derivada como `new` para resolver esta advertencia.

Para obtener más información, vea [New (nueva ranura en vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4487.

```cpp
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```