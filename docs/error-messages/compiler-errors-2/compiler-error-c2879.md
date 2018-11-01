---
title: Error del compilador C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 9ac8f5e5edb1a6ed7314c5b5d125fcc9bfbe67de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677960"
---
# <a name="compiler-error-c2879"></a>Error del compilador C2879

'símbolo': sólo un espacio de nombres existente se puede proporcionar un nombre alternativo mediante una definición de alias de espacio de nombres

No puede crear un [alias de espacio de nombres](../../cpp/namespaces-cpp.md#namespace_aliases) un símbolo que no sea un espacio de nombres.

El ejemplo siguiente genera C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```