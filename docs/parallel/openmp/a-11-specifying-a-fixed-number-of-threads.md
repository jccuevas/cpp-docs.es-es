---
title: A.11 especificando un número fijo de subprocesos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d09c470b76b61c6737566f7833334aeec6c63a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686544"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11 Especificar un número fijo de subprocesos
Algunos programas se basan en un número fijo, especificado previamente de subprocesos que se ejecuten correctamente.  Dado que la configuración predeterminada para el ajuste dinámico del número de subprocesos es definido por la implementación, estos programas pueden elegir desactivar la capacidad de subprocesos dinámica y establecer el número de subprocesos de forma explícita para garantizar la portabilidad. En el ejemplo siguiente se muestra cómo hacer esto con `omp_set_dynamic` ([sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39), y `omp_set_num_threads` ([punto 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36):  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 En este ejemplo, el programa se ejecutará correctamente solo si se ejecuta por 16 subprocesos. Si la implementación no es capaz de admitir 16 subprocesos, el comportamiento de este ejemplo es definido por la implementación.  
  
 Tenga en cuenta que el número de subprocesos que se ejecutan de una región paralela permanece constante durante una región paralela, sin tener en cuenta los subprocesos dinámicas establecer. El mecanismo de subprocesos dinámica determina el número de subprocesos que se utilizarán al principio de la región paralela y mantiene constante para la duración de la región.