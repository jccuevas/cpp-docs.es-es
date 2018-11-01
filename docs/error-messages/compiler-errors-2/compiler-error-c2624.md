---
title: Error del compilador C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: 407629ad2eecd0d3ca6081fefa59ddd60702f913
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456724"
---
# <a name="compiler-error-c2624"></a>Error del compilador C2624

las clases locales no se puede usar para declarar variables 'extern'

Una clase o estructura local no se puede usar para declarar `extern` variables.

El ejemplo siguiente genera C2624:

```
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```