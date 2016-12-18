---
title: "3.1.7 omp_set_dynamic Function | Microsoft Docs"
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
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.7 omp_set_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_set\_dynamic** habilita o deshabilita el ajuste dinámico de subprocesos disponibles para la ejecución de las regiones paralelas.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 Si *los dynamic\_threads* se evalúan como un valor distinto de cero, el número de subprocesos que se utilizan para ejecutar las regiones paralelas subsiguientes se puede ajustar automáticamente el entorno en tiempo de ejecución el mejor utiliza recursos del sistema.  En consecuencia, el número de subprocesos especificados por el usuario es el número de subprocesos máximo.  El número de subprocesos del equipo que ejecuta una región paralela permanece fijo para la duración de esa región paralela y es compatible con la función de **omp\_get\_num\_threads** .  
  
 si los *dynamic\_threads* evalúan a 0, se deshabilita el ajuste dinámico.  
  
 Esta función tiene efectos descritos anteriormente cuando se denomina de una parte del programa donde la función de **omp\_in\_parallel** devuelve cero.  Si se llama de una parte del programa donde la función de **omp\_in\_parallel** devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.  
  
 Una llamada a **omp\_set\_dynamic** tiene prioridad sobre la variable de entorno **OMP\_DYNAMIC** .  
  
 El valor predeterminado para el ajuste dinámico de subprocesos es implementación\-definido.  Como resultado, el código de usuario que dependen de un número concreto de subprocesos para la ejecución correcta deben deshabilitar explícitamente los subprocesos dinámicos.  Las implementaciones no deben proporcionar la capacidad de ajustar dinámicamente el número de subprocesos, pero se requieren para proporcionar la interfaz para admitir portabilidad en todas las plataformas.  
  
## referencias cruzadas:  
  
-   la función de**omp\_get\_num\_threads** , vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en la página 37.  
  
-   La variable de entorno**OMP\_DYNAMIC** , vea [sección 4,3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.  
  
-   la función de**omp\_in\_parallel** , vea [sección 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) en la página 38.