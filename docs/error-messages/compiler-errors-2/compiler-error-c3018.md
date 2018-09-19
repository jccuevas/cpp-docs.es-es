---
title: Error del compilador C3018 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3018
dev_langs:
- C++
helpviewer_keywords:
- C3018
ms.assetid: 685be45f-f116-43a8-a88d-05ab6616e2f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9813bd92834a2bc421b55c60eda2220ea14c7d97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079419"
---
# <a name="compiler-error-c3018"></a>Error del compilador C3018

'var1': el incremento o la prueba 'for' de OpenMP debe utilizar la variable de índice 'var2'

Un bucle `for` de una instrucción de OpenMP debe utilizar la misma variable para su comprobación y el incremento porque lo utiliza como su índice.

El ejemplo siguiente genera la advertencia C3018:

```
// C3018.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 5;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; j < 10; ++i)   // C3018
      // try the following line instead
      // for (i = 0; i < 10; ++i)
         j *= 2;

      #pragma omp for
      for (i = 0; i < 10; j = j + i)   // C3018
      // try the following line instead
      // for (i = 0; i < 10; i = j + i)
         j *= 2;
   }
}
```