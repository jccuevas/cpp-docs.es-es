---
title: Error del compilador C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: ff998beaa1d954f05a07d8ccf1b59cec0f4e3958
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737483"
---
# <a name="compiler-error-c2005"></a>Error del compilador C2005

\#línea esperaba un número de línea, se encontró ' token '

La Directiva de `#line` debe ir seguida de un número de línea.

En el ejemplo siguiente se genera C2005:

```cpp
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

Solución posible:

```cpp
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```
