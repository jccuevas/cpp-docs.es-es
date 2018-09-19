---
title: Error del compilador C3379 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90a4ccc17e63c21d4b6fb26e607450849f27b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109332"
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
