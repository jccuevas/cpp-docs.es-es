---
title: Error del compilador C2213
ms.date: 11/04/2016
f1_keywords:
- C2213
helpviewer_keywords:
- C2213
ms.assetid: ff012278-7f3b-4d49-aaed-2349756f6225
ms.openlocfilehash: 2a5f85adca30474ff8e60dc57694eba099b39387
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741344"
---
# <a name="compiler-error-c2213"></a>Error del compilador C2213

' Modifier ': argumento no válido para __based

El argumento que modifica `__based` no es válido.

En el ejemplo siguiente se genera C2213:

```cpp
// C2213.cpp
// compile with: /c
int i;
int *j;
char __based(i) *p;   // C2213
char __based(j) *p2;   // OK
```
