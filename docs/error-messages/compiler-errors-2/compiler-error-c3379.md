---
title: Error del compilador C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742904"
---
# <a name="compiler-error-c3379"></a>Error del compilador C3379

' Class ': una clase anidada no puede tener un especificador de acceso de ensamblado como parte de su declaración

Cuando se aplica a un tipo administrado, como Class o struct, las palabras clave [Public](../../cpp/public-cpp.md) y [Private](../../cpp/private-cpp.md) indican si la clase se expondrá a través de los metadatos del ensamblado. `public` o `private` no se pueden aplicar a una clase anidada, que heredará el acceso de ensamblado de la clase envolvente.

Cuando se usa con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), las palabras clave `ref` y `value` indican que una clase está administrada (vea [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

En el ejemplo siguiente se genera C3379:

```cpp
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
