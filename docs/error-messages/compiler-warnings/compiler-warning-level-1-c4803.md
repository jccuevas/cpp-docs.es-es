---
title: ADVERTENCIA del compilador (nivel 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: ebf7b3baec3519a142c7a1835aa15a980974bb48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052348"
---
# <a name="compiler-warning-level-1-c4803"></a>ADVERTENCIA del compilador (nivel 1) C4803

' Method ': el método raise tiene una clase de almacenamiento diferente de la del evento, ' Event '

Los métodos de evento deben tener la misma clase de almacenamiento que la declaración de evento. El compilador ajusta los métodos del evento para que las clases de almacenamiento sean las mismas.

Esta advertencia puede producirse si tiene una clase que implementa un evento de una interfaz. El compilador no genera implícitamente un método raise para un evento en una interfaz. Cuando se implementa esa interfaz en una clase, el compilador genera implícitamente un método raise y ese método no será virtual, por lo tanto, la advertencia. Para obtener más información sobre eventos, vea [Event](../../extensions/event-cpp-component-extensions.md).

Consulte pragma [Warning](../../preprocessor/warning.md) para obtener información sobre cómo desactivar una advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4803.

```cpp
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
