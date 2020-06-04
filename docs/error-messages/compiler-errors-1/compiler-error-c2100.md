---
title: Error del compilador C2100
ms.date: 11/04/2016
f1_keywords:
- C2100
helpviewer_keywords:
- C2100
ms.assetid: 9ed5ea11-9d55-4ddf-8b1a-162c74f3c390
ms.openlocfilehash: 08ff3b138db4ae07b73eb130983903cb60549e15
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752358"
---
# <a name="compiler-error-c2100"></a>Error del compilador C2100

direccionamiento indirecto no válido

El operador de direccionamiento indirecto (`*`) se aplica a un valor que no es de puntero.

En el ejemplo siguiente se genera C2100:

```cpp
// C2100.cpp
int main() {
   int r = 0, *s = 0;
   s = &r;
   *r = 200;   // C2100
   *s = 200;   // OK
}
```
