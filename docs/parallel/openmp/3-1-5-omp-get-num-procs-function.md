---
title: 3.1.5 omp_get_num_procs (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1632dfd4f84ad85a7ca1fbcfd80752d94ba2fda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428517"
---
# <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs (Función)

El `omp_get_num_procs` función devuelve el número de procesadores que están disponibles para el programa en el momento en que se llama a la función. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_num_procs(void);
```