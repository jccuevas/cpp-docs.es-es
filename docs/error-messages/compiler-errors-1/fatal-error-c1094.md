---
title: Error irrecuperable C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 23891a783a018f6d84ea820af98992f61632984c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366503"
---
# <a name="fatal-error-c1094"></a>Error irrecuperable C1094

'-Zmval1': opción de línea de comandos no es coherente con el valor utilizado para generar el encabezado precompilado ('-Zmval2')

El valor que se pasa a [/Yc](../../build/reference/yc-create-precompiled-header-file.md) debe ser el mismo valor que se pasa a [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm** valores deben ser el mismo en todas las compilaciones que usan o creación el mismo precompilado archivo de encabezado).

El ejemplo siguiente genera C1094:

```
// C1094.h
int func1();
```

Y luego,

```
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

Y luego,

```
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```