---
title: Error del compilador C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: b279202b8b32197a99d230040207aa50bc100495
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618483"
---
# <a name="compiler-error-c2013"></a>Error del compilador C2013

falta '>'

Una directiva `#include` carece de paréntesis angular de cierre. Agregue el paréntesis de cierre para resolver el error.

El ejemplo siguiente genera la advertencia C2013.

```
// C2013.cpp
#include <stdio.h    // C2013
```

Posible resolución:

```
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```