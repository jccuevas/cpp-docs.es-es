---
title: Error del compilador C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 2d6b2cb15cfaa0b72b946c0edb3b451737b51772
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553509"
---
# <a name="compiler-error-c3379"></a>Error del compilador C3379

'class': una clase anidada no puede tener un especificador de acceso de ensamblado como parte de su declaración.

Cuando se aplica a un tipo administrado, como una clase o estructura, el [pública](../../cpp/public-cpp.md) y [privada](../../cpp/private-cpp.md) palabras clave indican si la clase se expondrá a través de los metadatos del ensamblado. `public` o `private` no se puede aplicar a una clase anidada, que heredará el acceso al ensamblado de la clase envolvente.

Cuando se usa con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), `ref` y `value` palabras clave indican que una clase es administrada (vea [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md)).

El ejemplo siguiente genera C3379:

```
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
