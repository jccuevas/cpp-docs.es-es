---
title: Error del compilador C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: 251492b736ba3325ed263a9a8754fc8fa480c664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360234"
---
# <a name="compiler-error-c2748"></a>Error del compilador C2748

la creación de matrices administradas o WinRT debe disponer de un tamaño de matriz o un inicializador de matriz

Una matriz administrada o WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El ejemplo siguiente genera el error C2748 y muestra cómo corregirlo:

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```