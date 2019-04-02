---
title: Error del compilador C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: 516690f2524d48e7abbf7546592c6346e92c3e2e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781606"
---
# <a name="compiler-error-c3380"></a>Error del compilador C3380

'class': especificador de acceso de ensamblado no válido; solo se permiten 'public' o 'private'

Cuando se aplican a una clase o estructura administrada, las palabras clave [public](../../cpp/public-cpp.md) y [private](../../cpp/private-cpp.md) indican si la clase se expondrá a través de los metadatos del ensamblado. Solo `public` o `private` pueden aplicarse a una clase en un programa compilado con [/clr](../../build/reference/clr-common-language-runtime-compilation.md).

El `ref` y `value` palabras clave, cuando se usa con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), indican que una clase es administrada (vea [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

El ejemplo siguiente genera la advertencia C3380:

```
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```
