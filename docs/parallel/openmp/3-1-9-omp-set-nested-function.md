---
title: "3.1.9 omp_set_nested Function | Microsoft Docs"
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
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.9 omp_set_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_set\_nested** habilita o deshabilita el paralelismo anidados.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 Si *es anidados* se evalúa como 0, se deshabilita el paralelismo anidadas, que es el valor predeterminado, y regiones paralelas anidadas son serializadas y ejecutadas por el subproceso actual.  Si *es anidados* se evalúa como un valor distinto de cero, se habilita el paralelismo anidadas, y regiones en paralelo se anidan que pueden implementar subprocesos adicionales para formar a los equipos anidados.  
  
 Esta función tiene efectos descritos anteriormente cuando se denomina de una parte del programa donde la función de **omp\_in\_parallel** devuelve cero.  Si se llama de una parte del programa donde la función de **omp\_in\_parallel** devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.  
  
 Esta llamada tiene prioridad sobre la variable de entorno **OMP\_NESTED** .  
  
 Cuando se habilita el paralelismo anidado, el número de subprocesos utilizados para ejecutar las regiones paralelas anidadas es implementación\-definido.  Como resultado, las implementaciones de OpenMP\-conforme a se permiten serializar las regiones paralelas anidadas incluso cuando se habilita el paralelismo anidados.  
  
## referencias cruzadas:  
  
-   La variable de entorno**OMP\_NESTED** , vea [sección 4,4](../Topic/4.4%20OMP_NESTED.md) en la página 49.  
  
-   la función de**omp\_in\_parallel** , vea [sección 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) en la página 38.