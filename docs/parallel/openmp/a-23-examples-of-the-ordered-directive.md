---
title: A.23 Ejemplos de la directiva ordered
ms.date: 11/04/2016
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
ms.openlocfilehash: 2868b771fd57613981f3c6458b48493a1b26eee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472285"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23 Ejemplos de la directiva ordered

Es posible tener varias secciones ordenadas con una `for` especificado con el `ordered` cláusula. El primer ejemplo no es conforme porque la API especifica lo siguiente:

"Una iteración de un bucle con un `for` construcción no debe ejecutar el mismo `ordered` la directiva más de una vez y no deben ejecutar más de un `ordered` directiva." (Consulte [sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en la página 22)

En este ejemplo no compatible, todas las iteraciones ejecutan 2 secciones ordenadas:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

Muestra el siguiente ejemplo conforme un `for` con más de una sección ordenada:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```