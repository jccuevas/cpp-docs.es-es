---
title: Advertencia del compilador (nivel 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: d4eb7e7075c7adf418254e748f104a6d57c72741
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596630"
---
# <a name="compiler-warning-level-4-c4429"></a>Advertencia del compilador (nivel 4) C4429

posible incompleto o incorrectamente formado universal: nombre de carácter

El compilador detectó una secuencia de caracteres que puede ser un nombre de carácter universal mal formado. Es un nombre de carácter universal `\u` seguido de cuatro dígitos hexadecimales, o `\U` seguido de ocho dígitos hexadecimales.

El ejemplo siguiente genera C4429:

```
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```