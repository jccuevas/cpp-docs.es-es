---
title: Error del compilador C2940
ms.date: 11/04/2016
f1_keywords:
- C2940
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
ms.openlocfilehash: c5445b7083d11f1439d3e171d35c3ca39411310d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528796"
---
# <a name="compiler-error-c2940"></a>Error del compilador C2940

'class': el id. de clase de tipo se ha redefinido como typedef local

No puede usar una clase genérica o de plantilla como `typedef`local.

El ejemplo siguiente genera la advertencia C2940:

```
// C2940.cpp
template<class T>
struct TC {};
int main() {
   typedef int TC<int>;   // C2940
   typedef int TC;   // OK
}
```

También se puede producir C2940 al usar genéricos:

```
// C2940b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   typedef int GC<int>;   // C2940
   typedef int GC;
}
```