---
title: Error irrecuperable C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 99bfeea47ff46b6dadac9b32fa61306d54520d0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747402"
---
# <a name="fatal-error-c1094"></a>Error irrecuperable C1094

'-Zmval1 ': la opción de la línea de comandos no es coherente con el valor usado para compilar el encabezado precompilado ('-Zmval2 ')

El valor que se pasa a [/YC](../../build/reference/yc-create-precompiled-header-file.md) debe ser el mismo valor que se pasa a [/Yu](../../build/reference/yu-use-precompiled-header-file.md) ( **/ZM** valores debe ser el mismo en todas las compilaciones que usan o crean el mismo archivo de encabezado precompilado).

En el ejemplo siguiente se genera C1094:

```
// C1094.h
int func1();
```

Y luego,

```cpp
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

Y luego,

```cpp
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```
