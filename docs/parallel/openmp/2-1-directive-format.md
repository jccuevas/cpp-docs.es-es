---
title: 2.1 formato de directivas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2f2d2f5742dbc4faa1d8386e935c9d4ccc8049
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424656"
---
# <a name="21-directive-format"></a>2.1 Formato de directivas

La sintaxis de una directiva de OpenMP se especifican formalmente la gramática en [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)e informalmente como sigue:

```
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Cada directiva comienza con **#pragma omp**, para reducir la posibilidad de conflictos con otras directivas pragma de (que no sean de OpenMP o proveedor extensiones OpenMP) con los mismos nombres. El resto de la directiva sigue las convenciones de los estándares de C y C++ para las directivas de compilador. En concreto, se puede usar espacios en blanco antes y después la **#**, y a veces se debe usar un espacio en blanco para separar las palabras en una directiva. Después de los tokens de preprocesamiento el **#pragma omp** están sujetos a reemplazo de macros.

Directivas distinguen mayúsculas de minúsculas. El orden en que aparecen en las directivas no es significativo. Las cláusulas en las directivas se pueden repetir según sea necesario, sujeto a las restricciones que aparecen en la descripción de cada cláusula. Si *variable lista* aparece en una cláusula, deben especificar solo las variables. Solo un *nombre de directiva* se puede especificar por directiva.  Por ejemplo, no se permite la directiva siguiente:

```
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Se aplica una directiva de OpenMP a lo sumo una subsiguiente instrucción, que debe ser un bloque estructurado.