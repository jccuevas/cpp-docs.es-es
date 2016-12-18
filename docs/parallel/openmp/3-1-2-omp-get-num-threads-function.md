---
title: "3.1.2 omp_get_num_threads Function | Microsoft Docs"
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
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.2 omp_get_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_get\_num\_threads** devuelve el número de subprocesos actualmente en el equipo que ejecuta la región paralela de la que lo llama.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 La cláusula de **num\_threads** , la función de **omp\_set\_num\_threads** , y el control de la variable de entorno **OMP\_NUM\_THREADS** el número de subprocesos en un equipo.  
  
 Si el número de subprocesos no se ha establecido por el usuario, el valor predeterminado es implementación\-definido.  Esta función enlaza a **Paralelo** la directiva que agrega más próxima.  Si se llama de una parte de serie de un programa, o de una región paralela anidado que esté serializado, esta función devuelve 1.  
  
## referencias cruzadas:  
  
-   La variable de entorno**OMP\_NUM\_THREADS** , vea [sección 4,2](../../parallel/openmp/4-2-omp-num-threads.md) en la página 48.  
  
-   la cláusula de**num\_threads** , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.  
  
-   La construcción de**Paralelo** , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.