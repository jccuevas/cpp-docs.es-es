---
title: Error irrecuperable C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532675"
---
# <a name="fatal-error-c1018"></a>Error irrecuperable C1018

#elif inesperada

La directiva `#elif` aparece fuera de una construcción `#if`, `#ifdef`o `#ifndef` . Use `#elif` solamente dentro de una de estas construcciones.

El ejemplo siguiente genera la advertencia C1018:

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

Posible solución:

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```