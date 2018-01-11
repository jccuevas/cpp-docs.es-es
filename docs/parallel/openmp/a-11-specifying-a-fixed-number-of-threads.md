---
title: "A.11 especificando un número fijo de subprocesos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72c8aca2b90f021771ba9f9fc8a86d784ffe24a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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