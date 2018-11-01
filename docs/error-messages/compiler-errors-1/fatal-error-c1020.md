---
title: Error irrecuperable C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469815"
---
# <a name="fatal-error-c1020"></a>Error irrecuperable C1020

#endif inesperada

Una directiva `#endif` no tiene una directiva `#if`, `#ifdef`o `#ifndef` coincidente. Asegúrese de que cada `#endif` tenga una directiva coincidente.

El ejemplo siguiente genera la advertencia C1020:

```
// C1020.cpp
#endif     // C1020
```

Posible resolución:

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```