---
title: A.16 Usar bloqueos
ms.date: 11/04/2016
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
ms.openlocfilehash: 6afb94660acdc79ea5a7eb61d3bf7e21fd70d751
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458989"
---
# <a name="a16---using-locks"></a>A.16 Usar bloqueos

En el ejemplo siguiente, (para [sección 3.2](../../parallel/openmp/3-2-lock-functions.md) en la página 41) tenga en cuenta que el argumento de las funciones de bloqueo debe tener tipo `omp_lock_t`, y que no hay ninguna necesidad de vaciarlo.  Las funciones de bloqueo, hacer que los subprocesos estén inactivos mientras espera de entrada a la primera sección crítica, pero realice otro trabajo mientras se espera para que la segunda entrada.  El `omp_set_lock` bloques de función, pero el `omp_test_lock` función no es así, lo que permite el trabajo en skip() realizarse.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```