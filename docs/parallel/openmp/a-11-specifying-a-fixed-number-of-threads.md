---
title: "A.11   Specifying a Fixed Number of Threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.11   Specifying a Fixed Number of Threads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Algunos programas requieren un número fijo, especificado primero de subprocesos para ejecutarse correctamente.  Dado que la configuración predeterminada para el ajuste dinámico de subprocesos es implementación\-definido, tales programas pueden elegir para desactivar la capacidad dinámica de los subprocesos y establecer el número de subprocesos explícitamente para garantizar portabilidad.  El ejemplo siguiente se muestra cómo hacerlo mediante `omp_set_dynamic` \([sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39\), y `omp_set_num_threads` \([sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36\):  
  
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
  
 En este ejemplo, el programa se ejecuta correctamente sólo si es ejecutado por 16 subprocesos.  si la implementación no es capaz de admitir 16 subprocesos, el comportamiento de este ejemplo es implementación\-definido.  
  
 Observe que el número de subprocesos que ejecutan una región paralela permanece constante durante una región paralela, sin importar establecer dinámico de los subprocesos.  El mecanismo dinámico de subprocesos determina el número de subprocesos para usar el inicio de la región paralela y lo mantiene constante a lo largo de la región.