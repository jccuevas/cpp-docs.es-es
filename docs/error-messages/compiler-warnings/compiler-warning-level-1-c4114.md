---
title: Compilador advertencia (nivel 1) C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 41e951e7c4a8b23ddbec14c5421f66702e70c937
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450978"
---
# <a name="compiler-warning-level-1-c4114"></a>Compilador advertencia (nivel 1) C4114

el mismo calificador de tipo se ha utilizado más de una vez

Una definición o declaración de tipo utiliza un calificador de tipo (**const**, **volátil**, **firmado**, o **sin signo**) más de una vez. Esto hace que una advertencia con las extensiones de Microsoft (/Ze) y un error en la compatibilidad con ANSI (/Za).

El ejemplo siguiente genera C4114:

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

El ejemplo siguiente genera C4114:

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
