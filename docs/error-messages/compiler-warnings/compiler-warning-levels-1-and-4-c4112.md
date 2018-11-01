---
title: Advertencia del compilador (niveles 1 y 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: 3678d0ce5d9eb9568f0272da4173e72502b0557f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655837"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Advertencia del compilador (niveles 1 y 4) C4112

\#requiere que un número entero entre 1 y el número de línea

La directiva [#line](../../preprocessor/hash-line-directive-c-cpp.md) especifica un parámetro entero que está fuera del intervalo permitido.

Si el parámetro especificado es menor que 1, el contador de línea se restablece en 1. Si el parámetro especificado es mayor que *número*, que es el límite definido por el compilador, el contador de línea no se modifica. Esta es una advertencia de nivel 1 con la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia de nivel 4 con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

El ejemplo siguiente genera la advertencia C4112:

```
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```