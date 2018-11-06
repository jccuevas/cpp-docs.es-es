---
title: Compilador advertencia (nivel 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 11307ddc3b13a9cd9b36f1ee927082104792b07f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648362"
---
# <a name="compiler-warning-level-4-c4457"></a>Compilador advertencia (nivel 4) C4457

> declaración de '*identificador*' oculta el parámetro de función

La declaración de *identificador* en el ámbito local oculta la declaración del parámetro de función con un nombre idéntico. Esta advertencia le permite saber que las referencias a *identificador* en el ámbito local, resolver la versión declarada localmente, no el parámetro, que puede ser o no su intención. Para corregir este problema, se recomienda que proporcionar nombres de variables locales que no entren en conflicto con los nombres de parámetro.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4457 porque el parámetro `x` y la variable local `x` en `member_fn` tienen los mismos nombres. Para corregir este problema, use nombres diferentes para los parámetros y variables locales.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
