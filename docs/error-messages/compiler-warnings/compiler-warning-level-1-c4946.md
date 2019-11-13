---
title: ADVERTENCIA del compilador (nivel 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: 238e842202bfde05f41d5ab7bc4e3eb2b8b63735
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050203"
---
# <a name="compiler-warning-level-1-c4946"></a>ADVERTENCIA del compilador (nivel 1) C4946

se utilizó reinterpret_cast entre clases relacionadas: 'clase1' y 'clase2'

No use [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) para realizar conversiones entre tipos relacionados. Use [static_cast](../../cpp/static-cast-operator.md) en su lugar, o para los tipos polimórficos, use [dynamic_cast](../../cpp/dynamic-cast-operator.md).

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

En el ejemplo de código siguiente se genera C4946:

```cpp
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```