---
title: Error del compilador C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: 5b8712473631b16e2bbb47430966ccc0c552b9df
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739394"
---
# <a name="compiler-error-c2793"></a>Error del compilador C2793

' token ': token inesperado después de ':: '; se esperaba un identificador o una palabra clave ' Operator '

Los únicos tokens que pueden seguir `__super::` son un identificador o la palabra clave `operator`.

En el ejemplo siguiente se genera C2793

```cpp
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```
