---
title: 3.1.6 omp_in_parallel (función) | Documentos de Microsoft
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
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel (Función)
El **omp_in_parallel ()** función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela en ejecución en paralelo; de lo contrario, devuelve 0. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecutan en paralelo, incluidas las regiones anidadas que se serializan.