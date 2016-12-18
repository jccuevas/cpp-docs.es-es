---
title: "3.1.1 omp_set_num_threads Function | Microsoft Docs"
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
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.1 omp_set_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la función de `omp_set_num_threads` establece el número predeterminado de subprocesos para utilizar para las regiones paralelas subsiguientes que no especifican una cláusula de `num_threads` .  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 El valor *de los num\_threads* de parámetro debe ser un entero positivo.  Su efecto depende sobre si el ajuste dinámico de subprocesos está habilitado.  Para un conjunto completo de reglas sobre la interacción entre la función de `omp_set_num_threads` y el ajuste dinámico de subprocesos, vea la sección 2,3 de la página 8.  
  
 Esta función tiene efectos descritos anteriormente cuando se denomina de una parte del programa donde la función de `omp_in_parallel` devuelve cero.  Si se llama de una parte del programa donde la función de `omp_in_parallel` devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.  
  
 Esta llamada tiene prioridad sobre la variable de entorno `OMP_NUM_THREADS` .  El valor predeterminado para el número de subprocesos, que se pueden establecer llamando a `omp_set_num_threads` o estableciendo la variable de entorno `OMP_NUM_THREADS` , se puede reemplazar explícitamente en una única directiva de **Paralelo** especificando la cláusula de `num_threads` .  
  
## referencias cruzadas:  
  
-   la función de`omp_set_dynamic` , vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.  
  
-   la función de`omp_get_dynamic` , vea [sección 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) en la página 40.  
  
-   la variable de entorno`OMP_NUM_THREADS` , vea [sección 4,2](../../parallel/openmp/4-2-omp-num-threads.md) en la página 48, y la sección 2,3 de la página 8.  
  
-   la cláusula de`num_threads` , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8