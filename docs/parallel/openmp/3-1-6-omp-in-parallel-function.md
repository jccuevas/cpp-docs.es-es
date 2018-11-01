---
title: 3.1.6 omp_in_parallel (Función)
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482048"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel (Función)

El **omp_in_parallel ()** función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela que se ejecutan en paralelo; en caso contrario, devuelve 0. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_in_parallel(void);
```

Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecutan en paralelo, incluidas las regiones anidadas que se serializan.