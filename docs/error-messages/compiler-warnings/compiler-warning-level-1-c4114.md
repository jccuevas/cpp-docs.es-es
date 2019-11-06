---
title: ADVERTENCIA del compilador (nivel 1) C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 5662dba4339765db27d225eff2ad382ed56396ac
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626293"
---
# <a name="compiler-warning-level-1-c4114"></a>ADVERTENCIA del compilador (nivel 1) C4114

el mismo calificador de tipo se ha utilizado más de una vez

Una definición o declaración de tipo utiliza un calificador de tipo (**const**, **volatile**, **signed**o **unsigned**) más de una vez. Esto produce una advertencia con las extensiones de Microsoft (/ZE) y un error con compatibilidad con ANSI (/za).

En el ejemplo siguiente se genera C4114:

```cpp
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

En el ejemplo siguiente se genera C4114:

```cpp
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
