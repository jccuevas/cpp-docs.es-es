---
title: Error del compilador C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: b066e813203f10b902e49a62af97a9a041874752
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742124"
---
# <a name="compiler-error-c3020"></a>Error del compilador C3020

' var ': la variable de índice del bucle ' for ' de OpenMP no se puede modificar en el cuerpo del bucle

Un bucle de `for` de OpenMP no puede modificar el índice (contador de bucle) en el cuerpo del bucle de `for`.

En el ejemplo siguiente se genera C3020:

```cpp
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

Una variable declarada con [lastprivate](../../parallel/openmp/reference/lastprivate.md) no se puede utilizar como índice dentro de un bucle en paralelo.

En el ejemplo siguiente se proporcionará C3020 para el segundo lastprivate, ya que lastprivate desencadenará una escritura en idx_a dentro del bucle for más externo. La primera lastprivate no genera un error porque lastprivate desencadena una escritura en idx_a fuera del bucle for más externo (técnicamente, al final de la última iteración). En el ejemplo siguiente se genera C3020.

```cpp
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

En el ejemplo siguiente se muestra una posible solución:

```cpp
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
