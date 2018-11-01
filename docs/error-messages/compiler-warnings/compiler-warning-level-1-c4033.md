---
title: Advertencia del compilador (nivel 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: bef57d99ec9057f8b008deabda00b8a422a9e509
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443569"
---
# <a name="compiler-warning-level-1-c4033"></a>Advertencia del compilador (nivel 1) C4033

'function': la función debe devolver un valor

Esta función no devuelve ningún valor. Se devolvió un valor indefinido.

Las funciones que usan `return` sin un valor devuelto debe declararse como tipo `void`.

Este error corresponde al código de lenguaje C.

El ejemplo siguiente genera la advertencia C4033:

```
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```