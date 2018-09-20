---
title: 3.1.6 omp_in_parallel (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404623"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel (Función)

El **omp_in_parallel ()** función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela que se ejecutan en paralelo; en caso contrario, devuelve 0. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_in_parallel(void);
```

Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecutan en paralelo, incluidas las regiones anidadas que se serializan.