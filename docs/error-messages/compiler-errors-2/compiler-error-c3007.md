---
title: Error del compilador C3007
ms.date: 11/04/2016
f1_keywords:
- C3007
helpviewer_keywords:
- C3007
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
ms.openlocfilehash: 9b80cc556887bf04efa3d98a31ccfd7ed1a2e4d7
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302281"
---
# <a name="compiler-error-c3007"></a>Error del compilador C3007

'arg': la cláusula de la directiva 'directiva' de OpenMP no toma un argumento.

Una directiva de OpenMP tenía un argumento, pero la directiva no toma un argumento.

El ejemplo siguiente genera la advertencia C3007:

```c
// C3007.c
// compile with: /openmp
int main()
{
   #pragma omp parallel for ordered(2)   // C3007
}
```
