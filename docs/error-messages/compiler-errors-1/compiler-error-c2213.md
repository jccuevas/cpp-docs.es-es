---
title: Error del compilador C2213
ms.date: 11/04/2016
f1_keywords:
- C2213
helpviewer_keywords:
- C2213
ms.assetid: ff012278-7f3b-4d49-aaed-2349756f6225
ms.openlocfilehash: 125529aa23d43d9acd63652f73f636fee567f90a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400440"
---
# <a name="compiler-error-c2213"></a>Error del compilador C2213

'modifier': argumento para __based no válido

La modificación del argumento `__based` no es válido.

El ejemplo siguiente genera C2213:

```
// C2213.cpp
// compile with: /c
int i;
int *j;
char __based(i) *p;   // C2213
char __based(j) *p2;   // OK
```