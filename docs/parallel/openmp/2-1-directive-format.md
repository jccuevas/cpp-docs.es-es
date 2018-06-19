---
title: 2.1 formato de directivas | Documentos de Microsoft
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
ms.openlocfilehash: 1eec5a2f0e91df6e8d71797199bd3a3911a3aab0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687278"
---
# <a name="21-directive-format"></a>2.1 Formato de directivas
La sintaxis de una directiva de OpenMP formalmente especificada por la gramática de [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)e informalmente como se indica a continuación:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Cada directiva comienza con **#pragma omp**, para evitar posibles conflictos con otras directivas de pragma (extensiones de OpenMP no o proveedor con OpenMP) con los mismos nombres. El resto de la directiva sigue las convenciones de los estándares de C y C++ para las directivas de compilador. En concreto, puede usarse el espacio en blanco antes y después de la **#**, y a veces se debe usar el espacio en blanco para separar las palabras en una directiva. Después de tokens de preprocesamiento el **#pragma omp** están sujetos a reemplazo de macros.  
  
 Directivas distinguen mayúsculas de minúsculas. El orden en que aparecen las cláusulas en directivas no es significativo. Las cláusulas en las directivas se pueden repetir según sea necesario, sujeto a las restricciones indicadas en la descripción de cada cláusula. Si *lista de variables* aparece en una cláusula, deben especificar solo las variables. Solo un *nombre de directiva* se puede especificar por directiva.  Por ejemplo, no se permite la siguiente directiva:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 Se aplica una directiva de OpenMP a lo sumo una subsiguiente instrucción, que debe ser un bloque estructurado.