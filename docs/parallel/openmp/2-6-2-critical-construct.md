---
title: 2.6.2 critical (Construcción)
ms.date: 11/04/2016
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
ms.openlocfilehash: dcc0e6144be5daee2a225cda621db818e5a38e2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539079"
---
# <a name="262-critical-construct"></a>2.6.2 critical (Construcción)

El **críticos** directiva identifica una construcción que limita la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la **críticos** directiva es como sigue:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Opcional *nombre* puede utilizarse para identificar la región crítica. Los identificadores utilizados para identificar una región crítica tienen vinculación externa y se encuentran en un espacio de nombres que es independiente de los espacios de nombres utilizados por etiquetas, etiquetas, miembros y los identificadores normales.

Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso está ejecutando en una región crítica (en cualquier lugar en el programa) con el mismo nombre. Todo sin nombre **críticos** asignan directivas en el mismo nombre no especificado.