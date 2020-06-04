---
title: Error del compilador C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735936"
---
# <a name="compiler-error-c2061"></a>Error del compilador C2061

error de sintaxis: identificador ' Identifier '

El compilador encontró un identificador en el que no se esperaba. Asegúrese de que `identifier` se declara antes de usarlo.

Un inicializador puede estar entre paréntesis. Para evitar este problema, incluya el declarador entre paréntesis o conviértalo en `typedef`.

Este error también puede producirse cuando el compilador detecta una expresión como un argumento de plantilla de clase; Use [TypeName](../../cpp/typename.md) para indicar al compilador que es un tipo.

En el ejemplo siguiente se genera C2061:

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 puede producirse si se pasa un nombre de instancia a [typeid](../../extensions/typeid-cpp-component-extensions.md):

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
