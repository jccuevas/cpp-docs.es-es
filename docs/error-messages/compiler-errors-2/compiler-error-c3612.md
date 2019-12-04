---
title: Error del compilador C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 499c31b0c02bd72695cd6118612609a70316f0ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755751"
---
# <a name="compiler-error-c3612"></a>Error del compilador C3612

' type ': una clase sellada no puede ser abstracta

Los tipos definidos mediante `value` están sellados de forma predeterminada y una clase es abstracta a menos que implemente todos los métodos de su base. Una clase abstracta sellada no puede ser una clase base ni se puede crear una instancia de ella.

Para más información, vea [ref class and ref struct (C++/CLI and C++/CX)](../../extensions/classes-and-structs-cpp-component-extensions.md) [ref class y ref struct (C++/CLI y C++/CX)].

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3612:

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
