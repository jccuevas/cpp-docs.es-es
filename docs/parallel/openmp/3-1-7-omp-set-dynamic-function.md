---
title: "3.1.7 omp_set_dynamic (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1569235e807fb8e6981c45d7547cae7bd6f70c56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic (Función)
El **omp_set_dynamic ()** función habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones en paralelo. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 Si *dynamic_threads* se evalúa como un valor distinto de cero, se puede ajustar el número de subprocesos que se usan para ejecutar las siguientes regiones en paralelo automáticamente por el entorno de tiempo de ejecución para utilizar mejor los recursos del sistema. En consecuencia, el número de subprocesos especificados por el usuario es el número máximo de subprocesos. El número de subprocesos en el equipo que ejecuta una región paralela permanece fijo durante la duración de esa región paralela y notifica el **omp_get_num_threads ()** (función).  
  
 Si *dynamic_threads* se evalúa como 0, realizar un ajuste dinámico está deshabilitado.  
  
 Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde la **omp_in_parallel ()** función devuelve cero. Si se llama desde una parte del programa donde la **omp_in_parallel ()** función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.  
  
 Una llamada a **omp_set_dynamic ()** tiene prioridad sobre la **OMP_DYNAMIC** variable de entorno.  
  
 El valor predeterminado para el ajuste dinámico de subprocesos es definido por la implementación. Como resultado, los códigos de usuario que dependen de un número específico de subprocesos para su ejecución correcta deben deshabilitar explícitamente subprocesos dinámicos. Las implementaciones no son necesarias para garantizar la capacidad de ajuste dinámicamente el número de subprocesos, pero que son necesarias para proporcionar la interfaz para admitir la portabilidad en todas las plataformas.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **omp_get_num_threads ()** función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.  
  
-   **OMP_DYNAMIC** vea variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.  
  
-   **omp_in_parallel ()** función, vea [sección 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) en página 38.