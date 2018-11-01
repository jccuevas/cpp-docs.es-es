---
title: 2.6.3 barrier (Directiva)
ms.date: 11/04/2016
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
ms.openlocfilehash: 9079dce4b2a27e91e349fd0df8414d38cd245d2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637026"
---
# <a name="263-barrier-directive"></a>2.6.3 barrier (Directiva)

El **barrera** directiva sincroniza todos los subprocesos en un equipo. Cuando encuentra, cada subproceso en el equipo espera hasta que todos los demás han alcanzado este punto. La sintaxis de la **barrera** directiva es como sigue:

```
#pragma omp barrier new-line
```

Después de que todos los subprocesos en el equipo han detectado la barrera, cada subproceso en el equipo comienza a ejecutar las instrucciones después de la directiva de barrera en paralelo. Tenga en cuenta que dado que la **barrera** directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Consulte [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) para la gramática formal. El ejemplo siguiente muestra estas restricciones.

```
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```