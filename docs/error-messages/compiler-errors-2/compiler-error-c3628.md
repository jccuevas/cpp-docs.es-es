---
title: Error del compilador C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543785"
---
# <a name="compiler-error-c3628"></a>Error del compilador C3628

'clase base': administrada o WinRTclasses solo admiten herencia pública

Se intentó usar un administrado o WinRT de clase como un [privada](../../cpp/private-cpp.md) o [protegido](../../cpp/protected-cpp.md) clase base. Administrada o WinRT clase solo puede usarse como una clase base con [pública](../../cpp/public-cpp.md) acceso.

El ejemplo siguiente genera el error C3628 y muestra cómo corregirlo:

```
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
