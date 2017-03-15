---
title: "3.1.4 omp_get_thread_num Function | Microsoft Docs"
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
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.4 omp_get_thread_num Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de `omp_get_thread_num` devuelve el número de subprocesos, dentro de su equipo, el subproceso ejecutando la función.  El número de subproceso se encuentra entre 0 y **omp\_get\_num\_threads \(\)**– 1, incluidos.  El subproceso principal del equipo es el subproceso 0.  
  
 El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Si se llama de una región en serie, `omp_get_thread_num` devuelve 0.  Si se llama dentro de una región paralela anidado que esté serializado, esta función devuelve 0.  
  
## referencias cruzadas:  
  
-   la función de`omp_get_num_threads` , vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en la página 37.