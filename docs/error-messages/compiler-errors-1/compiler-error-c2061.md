---
title: Error del compilador C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 0bd1e770e38fcb85164bfa205470ac55a12e1c87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466201"
---
# <a name="compiler-error-c2061"></a>Error del compilador C2061

error de sintaxis: identificador 'identificador'

El compilador encontró un identificador que no se esperaba. Asegúrese de que `identifier` se declara antes de usarlo.

Un inicializador puede aparecer entre paréntesis. Para evitar este problema, escriba el declarador entre paréntesis o conviértalo en un `typedef`.

Este error también podría producirse cuando el compilador detecta una expresión como un argumento de plantilla de clase; usar [typename](../../cpp/typename.md) para indicar al compilador es un tipo.

El ejemplo siguiente genera C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 puede producirse si se pasa un nombre de instancia a [typeid](../../windows/typeid-cpp-component-extensions.md):

```
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