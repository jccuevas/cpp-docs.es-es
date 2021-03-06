---
title: Advertencia del compilador (nivel 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: ed4b8561975f3d808781551e0d5f363d0d0088b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991437"
---
# <a name="compiler-warning-level-4-c4263"></a>Advertencia del compilador (nivel 4) C4263

' función ': la función miembro no invalida ninguna función miembro virtual de clase base

Una definición de función de clase tiene el mismo nombre que una función virtual en una clase base, pero no el mismo número o tipo de argumentos. Esto oculta de forma eficaz la función virtual en la clase base.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

En el ejemplo siguiente se genera C4263:

```cpp
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```
