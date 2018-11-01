---
title: A.8 Especificar secciones paralelas
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461443"
---
# <a name="a8---specifying-parallel-sections"></a>A.8 Especificar secciones paralelas

En el ejemplo siguiente, (para [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14) funciones *valor*, *eje y*, y *zaxis* se puede ejecutar simultáneamente. La primera `section` directiva es opcional.  Tenga en cuenta que todos los `section` directivas deben aparecer en la extensión de léxico el `parallel sections` construir.

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```