---
title: 2.6.3 barrier (directiva) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429154"
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