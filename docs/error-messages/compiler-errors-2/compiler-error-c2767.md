---
title: Error del compilador C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 259e8a58abfa2dc5eacaa6c9f6e3d47b852f5c1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759820"
---
# <a name="compiler-error-c2767"></a>Error del compilador C2767

no coincide la dimensión administrada o WinRTarray: se esperaban N argumentos-M proporcionados

Una declaración de matriz administrada o de WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El siguiente ejemplo genera el error C2767 y muestra cómo corregirlo:

```cpp
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```
