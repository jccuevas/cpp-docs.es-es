---
title: Error del compilador C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: 0e2d8e70dcc9b23c56a321487cd4b933a1086387
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491278"
---
# <a name="compiler-error-c3020"></a>Error del compilador C3020

'var': variable de índice de 'bucle for' de OpenMP no puede modificarse en el cuerpo del bucle

OpenMP `for` bucle no puede modificar el índice (contador de bucle) en el cuerpo de la `for` bucle.

El ejemplo siguiente genera C3020:

```
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

Una variable declarada con [lastprivate](../../parallel/openmp/reference/lastprivate.md) no se puede usar como el índice dentro de un bucle en paralelo.

El siguiente ejemplo dará C3020 para el segundo lastprivate porque desencadenará una escritura en idx_a dentro de la más externa de bucle. La primera lastprivate no da error porque genera una escritura en idx_a fuera del extremo para el bucle (técnicamente, al final de la última iteración). El ejemplo siguiente genera C3020.

```
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

En el ejemplo siguiente se muestra una posible resolución:

```
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```