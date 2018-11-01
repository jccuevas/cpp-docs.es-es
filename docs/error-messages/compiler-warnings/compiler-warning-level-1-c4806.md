---
title: Advertencia del compilador (nivel 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578270"
---
# <a name="compiler-warning-level-1-c4806"></a>Advertencia del compilador (nivel 1) C4806

'operación': operación no segura: ningún valor del tipo 'tipo' promovido al tipo 'tipo' puede igualar la constante proporcionada.

Este mensaje advierte de código como `b == 3`, donde `b` tiene un tipo `bool`. Las reglas de promoción provocan que `bool` se promueva a `int`. Está permitido, pero nunca puede ser **true**. El ejemplo siguiente genera la advertencia C4806:

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```