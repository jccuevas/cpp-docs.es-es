---
title: "4.2 OMP_NUM_THREADS | Microsoft Docs"
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
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.2 OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La variable de entorno **OMP\_NUM\_THREADS** establece el número predeterminado de subprocesos para utilizar durante la ejecución, a menos que ese número explícitamente es cambiado llamando a la rutina de biblioteca de **omp\_set\_num\_threads** o por una cláusula explícita de **num\_threads** en una directiva de **Paralelo** .  
  
 El valor de la variable de entorno **OMP\_NUM\_THREADS** debe ser un entero positivo.  Su efecto depende sobre si el ajuste dinámico de subprocesos está habilitado.  Para un conjunto completo de reglas sobre la interacción entre la variable de entorno **OMP\_NUM\_THREADS** y el ajuste dinámico de subprocesos, vea la sección 2,3 de la página 8.  
  
 Si no se especifica ningún valor para la variable de entorno **OMP\_NUM\_THREADS** , o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos el sistema puede admitir, el número de subprocesos para utilizar es implementación\-definido.  
  
 Ejemplo:  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## referencias cruzadas:  
  
-   la cláusula de**num\_threads** , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.  
  
-   la función de**omp\_set\_num\_threads** , vea [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.  
  
-   la función de**omp\_set\_dynamic** , vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.