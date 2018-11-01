---
title: Del compilador (nivel 4) de la advertencia C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: 006628721598d838070412c895f64b9a8d3de4e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452590"
---
# <a name="compiler-warning-level-4-c4456"></a>Del compilador (nivel 4) de la advertencia C4456

> declaración de '*identificador*' oculta la declaración local anterior

La declaración de *identificador* en el ámbito local oculta la declaración de la declaración local anterior del mismo nombre. Esta advertencia le permite saber que las referencias a *identificador* en el ámbito local, resolver la versión declarada localmente, no el local anterior, que puede ser o no su intención. Para corregir este problema, se recomienda que proporcionar nombres de variables locales que no entren en conflicto con otros nombres locales.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4456 porque la variable de control de bucle `int x` y la variable local `double x` en `member_fn` tienen los mismos nombres. Para corregir este problema, use nombres diferentes para las variables locales.

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
