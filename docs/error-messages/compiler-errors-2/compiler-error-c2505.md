---
title: Error del compilador C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: 94a6f180c93839646d771509145b2f65a00780fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746869"
---
# <a name="compiler-error-c2505"></a>Error del compilador C2505

' Symbol ': ' __declspec (modificador) ' solo se puede aplicar a declaraciones o definiciones de objetos globales o miembros de datos estáticos

En una función se utilizó un modificador `__declspec` diseñado para usarse únicamente en el ámbito global.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

En el ejemplo siguiente se genera C2505:

```cpp
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```
