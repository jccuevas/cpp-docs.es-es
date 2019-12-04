---
title: Error del compilador C2940
ms.date: 11/04/2016
f1_keywords:
- C2940
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
ms.openlocfilehash: 9477a2da32040db67a143a59d940c5f1cbe94904
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740447"
---
# <a name="compiler-error-c2940"></a>Error del compilador C2940

'class': el id. de clase de tipo se ha redefinido como typedef local

No puede usar una clase genérica o de plantilla como `typedef`local.

El ejemplo siguiente genera la advertencia C2940:

```cpp
// C2940.cpp
template<class T>
struct TC {};
int main() {
   typedef int TC<int>;   // C2940
   typedef int TC;   // OK
}
```

También se puede producir C2940 al usar genéricos:

```cpp
// C2940b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   typedef int GC<int>;   // C2940
   typedef int GC;
}
```
