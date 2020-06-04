---
title: Error del compilador C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6c7238faf94a2493894534ae5684634b65bb4342
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736300"
---
# <a name="compiler-error-c2879"></a>Error del compilador C2879

' Symbol ': solo se puede asignar un nombre alternativo a un espacio de nombres existente mediante una definición de alias de espacio de nombres

No se puede crear un [alias de espacio de nombres](../../cpp/namespaces-cpp.md#namespace_aliases) para un símbolo que no sea un espacio de nombres.

En el ejemplo siguiente se genera C2879:

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
