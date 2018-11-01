---
title: Advertencia del compilador (nivel 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: b8f24df7465525b24ecd3871447bd873889b1e23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583812"
---
# <a name="compiler-warning-level-1-c4618"></a>Advertencia del compilador (nivel 1) C4618

parámetros de tipo pragma incluían una cadena vacía; se ha omitido pragma

Se proporcionó una cadena nula como argumento a un **#pragma**.

Se procesó la directiva pragma sin el argumento.

El ejemplo siguiente genera C4618:

```
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```