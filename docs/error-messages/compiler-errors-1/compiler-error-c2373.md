---
title: Error del compilador C2373
ms.date: 11/04/2016
f1_keywords:
- C2373
helpviewer_keywords:
- C2373
ms.assetid: 7a08bf0b-852d-48be-ba75-70df9f4b5951
ms.openlocfilehash: ede21bd2dfba5654cb1c636003fb3cea6a3149e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745569"
---
# <a name="compiler-error-c2373"></a>Error del compilador C2373

'identifier': nueva definición; modificadores de tipo distintos

El identificador ya está definido con un modificador de tipo diferente.

El ejemplo siguiente genera la advertencia C2373:

```
// C2373.h
void __clrcall func( void );
const int i = 20;
```

Y después:

```cpp
// C2373.cpp
// compile with: /c
#include "C2373.h"
extern void __cdecl func( void );   // C2373
extern void __clrcall func( void );   // OK

extern int i;   // C2373
extern const int i;   // OK
```
