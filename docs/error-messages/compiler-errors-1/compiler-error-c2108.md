---
title: Error del compilador C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: 069f369627f42314cc14688a9e0c0a55808db507
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752033"
---
# <a name="compiler-error-c2108"></a>Error del compilador C2108

el subíndice no es de tipo entero

El subíndice de la matriz es una expresión no entera.

## <a name="example"></a>Ejemplo

C2108 puede producirse si se usa incorrectamente el puntero `this` de un tipo de valor para tener acceso al indizador predeterminado del tipo. Para obtener más información, vea [semántica del puntero this](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

En el ejemplo siguiente se genera C2108.

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
