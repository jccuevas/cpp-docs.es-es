---
title: A.23 ejemplos de la directiva ordered | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405975"
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