---
title: Error del compilador C2459
ms.date: 11/04/2016
f1_keywords:
- C2459
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
ms.openlocfilehash: d2e8b375fd1219b11b3a543bf3a565ddee00ccf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367959"
---
# <a name="compiler-error-c2459"></a>Error del compilador C2459

'identifier': se está definiendo; no se puede agregar como miembro anónimo

Una clase, estructura o unión se ha redefinido en su propio ámbito por un miembro de una unión anónima.

El ejemplo siguiente genera C2459:

```
// C2459.cpp
// compile with: /c
class C {
   union { int C; };   // C2459
   union { int D; };
};
```