---
title: "2.3 parallel (construcción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb1d43207e7276aadac32e38a43cfa4ae47b9186
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="23-parallel-construct"></a>2.3 parallel (Construcción)
La directiva siguiente define una región paralela, que es una región del programa que va a ser ejecutado por varios subprocesos en paralelo. Ésta es la construcción fundamental que se inicia la ejecución en paralelo.  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block  
```  
  
 El *cláusula* es uno de los siguientes:  
  
 **Si (** *expresión escalar* **)**  
  
 **privada (** *lista de variables* **)**  
  
 **firstprivate (** *lista de variables* **)**  
  
 **predeterminado (compartido &#124; ninguno)**  
  
 **compartido (** *lista de variables* **)**  
  
 **copyin (** *lista de variables* **)**  
  
 **reducción (** *operador* **:***lista de variables* **)**   
  
 **num_threads (** *expresión de tipo entero* **)**  
  
 Cuando un subproceso encuentra una construcción paralela, se crea un grupo de subprocesos si se cumple alguna de los casos siguientes:  
  
-   Ya no **si** cláusula está presente.  
  
-   El **si** expresión se evalúa como un valor distinto de cero.  
  
 Este subproceso se convierte en el subproceso principal del equipo, con un número de subprocesos de 0, y todos los subprocesos en el equipo, incluido el subproceso principal, la región se ejecutan en paralelo. Si el valor de la **si** expresión es cero, se serializa la región.  
  
 Para determinar el número de subprocesos que se solicitan, se considerarán las reglas siguientes en orden. Se aplicará la primera regla cuya condición se cumple:  
  
1.  Si el **num_threads** cláusula está presente, el valor de la expresión de entero es el número de subprocesos que se solicita.  
  
2.  Si el **omp_set_num_threads ()** función de biblioteca se ha llamado, entonces el valor del argumento en la llamada ha ejecutado más recientemente es el número de subprocesos que se solicita.  
  
3.  Si la variable de entorno **OMP_NUM_THREADS** se define, el valor de esta variable de entorno es el número de subprocesos que se solicita.  
  
4.  Si ninguno de los métodos anteriores se han utilizado, el número de subprocesos solicitado es definido por la implementación.  
  
 Si el **num_threads** cláusula está presente, a continuación, sustituye el número de subprocesos solicitado por el **omp_set_num_threads ()** función de biblioteca o el **OMP_NUM_THREADS** se aplica a la variable de entorno solo para la región paralela. Regiones en paralelo posteriores no se ven afectadas por ella.  
  
 El número de subprocesos que se ejecutan en la región paralela también depende de si está habilitado el ajuste dinámico del número de subprocesos. Si se deshabilita el ajuste dinámico, el número solicitado de subprocesos ejecutará la región paralela. Si está habilitado el ajuste dinámico del número solicitado de subprocesos es el número máximo de subprocesos que puede ejecutar la región paralela.  
  
 Si una región paralela se encontró al realizar un ajuste dinámico del número de subprocesos está deshabilitado y el número de subprocesos solicitado para la región paralela supera el número que puede proporcionar el sistema en tiempo de ejecución, el comportamiento del programa es definido por la implementación. Una implementación por ejemplo, podría interrumpir la ejecución del programa, o puede serializar la región paralela.  
  
 El **omp_set_dynamic ()** función de biblioteca y el **OMP_DYNAMIC** variable de entorno puede utilizarse para habilitar y deshabilitar el ajuste dinámico del número de subprocesos.  
  
 El número de procesadores físicos realmente alojan los subprocesos en un momento dado es definido por la implementación. Una vez creado, el número de subprocesos en el equipo permanece constante para la duración de esa región paralela. Se puede cambiar explícitamente por el usuario o automáticamente por el sistema de tiempo de ejecución de una región paralela a otro.  
  
 Las instrucciones incluidas en la extensión dinámica de la región paralela se ejecutan por cada subproceso, y cada subproceso puede ejecutar una ruta de acceso de las instrucciones que es diferente de los demás subprocesos. Las directivas que se encuentra fuera de la extensión léxica de una región paralela se conocen como directivas de huérfanas.  
  
 Hay una barrera implícita al final de una región paralela. Solo el subproceso principal del equipo continúa la ejecución al final de una región paralela.  
  
 Si un subproceso en un equipo que ejecuta una región paralela encuentra otra construcción paralela, crea un nuevo equipo y se convierte en el maestro de ese nuevo equipo. Regiones anidadas en paralelo se serializan de forma predeterminada. Como resultado, de forma predeterminada, una región paralela anidada se ejecuta mediante un equipo que se compone de un subproceso. El comportamiento predeterminado puede cambiarse mediante la función de biblioteca de tiempo de ejecución **omp_set_nested ()** o la variable de entorno **OMP_NESTED**. Sin embargo, el número de subprocesos en un equipo que ejecute una región paralela anidada es definido por la implementación.  
  
 Restricciones a la **paralelo** directiva son los siguientes:  
  
-   A lo sumo una **si** cláusula puede aparecer en la directiva.  
  
-   No se especifica si cualquier lado efectos dentro de la if expresión o **num_threads** expresión se producen.  
  
-   A **throw** ejecuta dentro de una región paralela debe provocar que la ejecución reanudar dentro de la extensión dinámica del mismo bloque estructurado y debe capturarse por el mismo subproceso que produjo la excepción.  
  
-   Solo una **num_threads** cláusula puede aparecer en la directiva. El **num_threads** expresión se evalúa fuera del contexto de la región paralela y se debe evaluar como un valor entero positivo.  
  
-   El orden de evaluación de la **si** y **num_threads** cláusulas no está especificado.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **privada**, **firstprivate**, **predeterminado**, **compartido**, **copyin**, y **reducción**cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.  
  
-   **OMP_NUM_THREADS** variable de entorno, [sección 4.2](../../parallel/openmp/4-2-omp-num-threads.md) en página 48.  
  
-   **omp_set_dynamic ()** función de biblioteca, consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.  
  
-   **OMP_DYNAMIC** vea variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.  
  
-   **omp_set_nested ()** función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.  
  
-   **OMP_NESTED** vea variable de entorno [sección 4.4](../../parallel/openmp/4-4-omp-nested.md) en la página 49.  
  
-   **omp_set_num_threads ()** función de biblioteca, consulte [punto 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.