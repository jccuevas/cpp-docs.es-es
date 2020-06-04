---
title: Error del compilador C3010
ms.date: 11/04/2016
f1_keywords:
- C3010
helpviewer_keywords:
- C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
ms.openlocfilehash: cbce65840280d3171ea84638b968686fa65633be
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302255"
---
# <a name="compiler-error-c3010"></a>Error del compilador C3010

'etiqueta': no se permiten saltos fuera de un bloque estructurado de OpenMP.

No se puede saltar dentro o fuera del código un bloque OpenMP.

El ejemplo siguiente genera la advertencia C3010:

```c
// C3010.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
      #pragma omp parallel
      {
         goto lbl3;
      }
   }
   lbl3:;   // C3010
}
```
