---
title: Advertencia del compilador (nivel 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 743069c0ed3103a2ed8d459def65083146b971e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497043"
---
# <a name="compiler-warning-level-4-c4487"></a>Advertencia del compilador (nivel 4) C4487

'función_de_clase_derivada': coincide con el método no virtual heredado 'función_de_clase_base' pero no está explícitamente marcado como 'new'

Una función en una clase derivada tiene la misma firma que una función de la clase base no virtuales. C4487 le recuerda que la función de la clase derivada no reemplaza la función de la clase base. Marcar explícitamente la función de la clase derivada como `new` para resolver esta advertencia.

Para obtener más información, consulte [new (nueva ranura en vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4487.

```
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