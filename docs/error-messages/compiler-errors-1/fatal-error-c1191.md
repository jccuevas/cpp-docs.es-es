---
title: Error irrecuperable C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: 89af73699120ee4d8af3cda746727d758ef6d22c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609669"
---
# <a name="fatal-error-c1191"></a>Error irrecuperable C1191

solo se puede importar 'dll' en el ámbito global

La instrucción para importar mscorlib.dll en un programa que utiliza programación /clr no puede aparecer en un espacio de nombres o una función, pero debe aparecer en el ámbito global.

El ejemplo siguiente genera C1191:

```
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Posible resolución:

```
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```