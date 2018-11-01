---
title: 2.5.1 parallel for (Construcción)
ms.date: 11/04/2016
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
ms.openlocfilehash: e74fa958a70fb10aadd39ccc6b4e56670bc072b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590338"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for (Construcción)

El **paralelas para** directiva es un acceso directo para un **paralelo** región que contiene una sola **para** directiva. La sintaxis de la **paralelas para** directiva es como sigue:

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Esta directiva permite que todas las cláusulas de la **paralelo** directiva y la **para** la directiva, excepto el `nowait` cláusula con significados idénticos y restricciones. La semántica es idéntica a la especificación explícita de un **paralelo** directiva seguido inmediatamente por un **para** directiva.

## <a name="cross-references"></a>Referencias cruzadas:

- **paralelo** la directiva, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **para** la directiva, consulte [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11.

- Cláusulas de atributos de datos, vea [2.7.2 cláusulas de atributos de uso compartido de datos](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.