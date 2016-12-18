---
title: "3.1.3 omp_get_max_threads Function | Microsoft Docs"
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
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.3 omp_get_max_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_get\_max\_threads** devuelve un entero que se garantice para ser por lo menos tan grande como el número de subprocesos que se utilizan para formar un equipo si se encontró una región paralela sin una cláusula de **num\_threads** en ese momento en el código.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 A continuación expresar un límite inferior en el valor de **omp\_get\_max\_threads**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 Tenga en cuenta que si una región paralela subsiguiente utiliza la cláusula de **num\_threads** para solicitar un número concreto de subprocesos, la garantía en el límite inferior del resultado de **omp\_get\_max\_threads** que ningún largo mantiene.  
  
 El valor devuelto de la función de **omp\_get\_max\_threads** se puede utilizar para asignar dinámicamente el suficiente almacenamiento para todos los subprocesos del equipo formado en la región paralela subsiguiente.  
  
## referencias cruzadas:  
  
-   la función de**omp\_get\_num\_threads** , vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en la página 37.  
  
-   la función de**omp\_set\_num\_threads** , vea [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.  
  
-   la función de**omp\_set\_dynamic** , vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.  
  
-   la cláusula de**num\_threads** , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.