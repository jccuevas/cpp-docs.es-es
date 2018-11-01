---
title: Error del compilador C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: c02d7216df42681ae2ec733ae932d22861c1f0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572017"
---
# <a name="compiler-error-c2646"></a>Error del compilador C2646

Una unión o un struct anónimo en un ámbito global o de espacio de nombres se debe declarar como static

Una unión o un struct anónimo tiene un ámbito global o de espacio de nombres pero no se ha declarado como `static`.

El ejemplo siguiente genera el error C2646 y muestra cómo corregirlo:

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```