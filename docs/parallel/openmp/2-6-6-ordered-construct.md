---
title: 2.6.6 ordered (Construcción)
ms.date: 11/04/2016
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
ms.openlocfilehash: fe6ad4adf2a4fcccfefe3c3585d9c88c0a118931
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615805"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered (Construcción)

El bloque estructurado que sigue un **ordenados** directiva se ejecuta en el orden en el que se ejecutan en un bucle secuencial iteraciones. La sintaxis de la **ordenados** directiva es como sigue:

```
#pragma omp ordered new-linestructured-block
```

Un **ordenados** directiva debe estar dentro de la extensión dinámica de un **para** o **paralelas para** construir. El **para** o **paralelas para** la directiva a la que el **ordenados** construcción enlaza debe tener un **ordenados** cláusula especificada como se describe en [Sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11. En la ejecución de un **para** o **paralelas para** construir con un **ordenados** cláusula, **ordenados** construcciones se ejecutan de forma estricta en el orden en el que se ejecutaría en una ejecución secuencial del bucle.

Restricciones para el **ordenados** directiva son los siguientes:

- Una iteración de un bucle con un **para** construcción no debe ejecutar la misma directiva ordered más de una vez y no debe ejecutar más de un **ordenados** directiva.