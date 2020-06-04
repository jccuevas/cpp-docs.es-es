---
title: Error del compilador C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: d589094f117135474d1a8788867d2d571bbb5f5d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739550"
---
# <a name="compiler-error-c2791"></a>Error del compilador C2791

uso no válido de ' Super ': ' clase ' no tiene clases base

La palabra clave [Super](../../cpp/super.md) se usó en el contexto de una función miembro de una clase que no tiene ninguna clase base.

En el ejemplo siguiente se genera C2791:

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
