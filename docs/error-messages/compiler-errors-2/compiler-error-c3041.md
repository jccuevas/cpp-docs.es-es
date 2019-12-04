---
title: Error del compilador C3041
ms.date: 11/04/2016
f1_keywords:
- C3041
helpviewer_keywords:
- C3041
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
ms.openlocfilehash: f9f9b9a598760b251d911f3f0a5ddd1114dd764c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754945"
---
# <a name="compiler-error-c3041"></a>Error del compilador C3041

'var': la variable de la cláusula 'copyprivate' debe ser privada en el contexto envolvente

Una variable que se pase a [copyprivate](../../parallel/openmp/reference/copyprivate.md) no se puede compartir en el contexto envolvente.

El ejemplo siguiente genera la advertencia C3041:

```cpp
// C3041.cpp
// compile with: /openmp /c
#include "omp.h"
double d;
int main() {
   #pragma omp parallel shared(d)
   // try the following line instead
   // #pragma omp parallel private(d)
   {
      // or don't make d copyprivate
      #pragma omp single copyprivate(d)   // C3041
      {
      }
   }
}
```
