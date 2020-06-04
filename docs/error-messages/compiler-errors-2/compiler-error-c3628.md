---
title: Error del compilador C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755829"
---
# <a name="compiler-error-c3628"></a>Error del compilador C3628

' clase base ': WinRTclasses administrado o solo admiten herencia pública

Se intentó usar una clase administrada o WinRT como una clase base [privada](../../cpp/private-cpp.md) o [protegida](../../cpp/protected-cpp.md) . Una clase administrada o WinRT solo se puede usar como clase base con acceso [público](../../cpp/public-cpp.md) .

El ejemplo siguiente genera el error C3628 y muestra cómo corregirlo:

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
