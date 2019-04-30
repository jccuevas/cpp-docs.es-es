---
title: Error del compilador C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 4d935e140d89cb5c3714450597677a7a02a245e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385490"
---
# <a name="compiler-error-c3894"></a>Error del compilador C3894

'var': uso de valor l del miembro de datos estático initonly solamente se permite en el constructor de clase 'class'

Estática [initonly](../../dotnet/initonly-cpp-cli.md) los miembros de datos solo pueden usarse como valores l en su punto de declaración o en un constructor estático.

Los miembros de datos de instancia (no estáticos) initonly solo pueden usarse como valores l en su punto de declaración o en los constructores de instancia (no estáticos).

El ejemplo siguiente genera C3894:

```
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```