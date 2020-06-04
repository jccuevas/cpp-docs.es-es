---
title: Error del compilador C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 77a9122d20561ceee4f211394b3b81900d5580ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756089"
---
# <a name="compiler-error-c2658"></a>Error del compilador C2658

' Member ': nueva definición en struct/union anónimos

Dos estructuras o uniones anónimas contenían declaraciones de miembros con el mismo identificador pero con tipos diferentes. En [/za](../../build/reference/za-ze-disable-language-extensions.md), también recibirá este error para los miembros con el mismo identificador y tipo.

En el ejemplo siguiente se genera C2658:

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```
