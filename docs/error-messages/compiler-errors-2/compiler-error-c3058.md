---
title: Error del compilador C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 5655fe8ebeb8f1b61d7acbba5313c2e3ab2a2b4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265638"
---
# <a name="compiler-error-c3058"></a>Error del compilador C3058

'symbol': símbolo no declarado como 'threadprivate' antes de utilizarse en la cláusula 'copyin'

Un símbolo se debe declarar primero como [threadprivate](../../parallel/openmp/reference/threadprivate.md) antes de poderlo utilizar en una cláusula [copyin](../../parallel/openmp/reference/copyin.md) .

El ejemplo siguiente genera la advertencia C3058:

```
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

Posible resolución:

```
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```