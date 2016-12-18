---
title: "2.3 parallel Construct | Microsoft Docs"
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
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.3 parallel Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva siguiente define una región paralela, que es un área de programa que debe ejecutarse por varios subprocesos en paralelo.  ésta es la construcción fundamental que comienza la ejecución paralela.  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line  
   structured-block  
```  
  
 *La cláusula* es:  
  
 *expresión escalar* **\)**de**si \(**  
  
 *variable\-lista* **\)**de**private \(**  
  
 *variable\-lista* **\)**de**firstprivate \(**  
  
 **valor predeterminado \(compartido &#124; ninguno\)**  
  
 *variable\-lista* **\)**de**compartido \(**  
  
 *variable\-lista* **\)**de**copyin \(**  
  
 *variable\-lista* **\)**de**:** de*operador de***detallado \(**  
  
 *expresión de tipo entero* **\)**de**num\_threads \(**  
  
 Cuando un subproceso encuentra una construcción paralela, un equipo de subprocesos se crea si uno de los casos siguientes:  
  
-   No hay ninguna cláusula de **If \[SQL2008\]** presente.  
  
-   La expresión de **If \[SQL2008\]** se evalúa como un valor distinto de cero.  
  
 Este subproceso se convierte en el subproceso principal del equipo, con un número de subproceso de 0, y todos los subprocesos del equipo, incluido el subproceso principal, ejecutan la región en paralelo.  Si el valor de la expresión de **If \[SQL2008\]** es cero, la región se serializada.  
  
 Para determinar el número de subprocesos se soliciten que, las reglas siguientes se considerarán en orden.  La primera regla cuyas se cumple condición se aplicará:  
  
1.  Si la cláusula de **num\_threads** está presente, el valor de la expresión de entero es el número de subprocesos solicitados.  
  
2.  Si se ha llamado a la función de biblioteca de **omp\_set\_num\_threads** , el valor del argumento en la llamada ejecutada más recientemente es el número de subprocesos solicitados.  
  
3.  Si la variable de entorno **OMP\_NUM\_THREADS** está definido, el valor de esta variable de entorno es el número de subprocesos solicitados.  
  
4.  Si no se utilizara ninguno de los métodos anteriores, el número de subprocesos solicitados es implementación\-definido.  
  
 Si la cláusula de **num\_threads** está presente a continuación reemplaza el número de subprocesos solicitados por la función de biblioteca de **omp\_set\_num\_threads** o la variable de entorno **OMP\_NUM\_THREADS** sólo para la región paralela que se aplica a.  Las regiones paralelas subsiguientes no se ven afectadas por ella.  
  
 El número de subprocesos que se ejecutan la región paralela también depende sobre si el ajuste dinámico de subprocesos está habilitado.  Si se deshabilita el ajuste dinámico, el número solicitado de subprocesos se ejecutará la región paralela.  Si el ajuste dinámico se habilita el número solicitado de subprocesos es el número máximo de subprocesos que pueden ejecutar la región paralela.  
  
 Si se encuentra una región paralela mientras el ajuste dinámico de subprocesos está deshabilitado, y el número de subprocesos solicitados para la región paralela supera el número que el sistema de motor en tiempo de ejecución puede proporcionar, el comportamiento del programa es implementación\-definido.  Una implementación puede, por ejemplo, interrumpir la ejecución del programa, o puede serializar la región paralela.  
  
 La función de biblioteca de **omp\_set\_dynamic** y la variable de entorno **OMP\_DYNAMIC** se pueden utilizar para habilitar y deshabilitar el ajuste dinámico de subprocesos.  
  
 El número de procesadores físicos que hospedan realmente los subprocesos en un momento determinado implementación\-definido.  Una vez creado, el número de subprocesos del equipo permanece constante para la duración de esa región paralela.  Puede cambiar explícitamente por el usuario o automáticamente por el sistema en tiempo de ejecución desde una región paralela a otra.  
  
 Las instrucciones contenidas dentro de la extensión dinámica de la región paralela se ejecutan en cada subproceso, y cada subproceso puede ejecutar una ruta de instrucciones diferente de otros subprocesos.  Las directivas que se encuentran fuera de la extensión léxica de una región paralela se denominan directivas dejadas huérfano.  
  
 Hay una barrera implícitamente al final de una región paralela.  Sólo el subproceso principal del equipo continúa la ejecución al final de una región paralela.  
  
 Si un subproceso en un equipo que ejecuta una región paralela encuentra otra construcción paralela, crea un nuevo equipo, y se convierte master de ese nuevo equipo.  Las regiones paralelas anidadas son serializadas de forma predeterminada.  Por consiguiente, de forma predeterminada, una región paralela anidado es ejecutada por un equipo compuesto por un subproceso.  El comportamiento predeterminado se puede cambiar mediante la función de biblioteca en tiempo de ejecución **omp\_set\_nested** o la variable de entorno **OMP\_NESTED**.  sin embargo, el número de subprocesos en un equipo que ejecuten una región paralela anidado es implementación\-definido.  
  
 Restricciones de la directiva de **Paralelo** son los siguientes:  
  
-   A lo sumo una cláusula de **If \[SQL2008\]** puede aparecer en la directiva.  
  
-   No se especifica si cualquier efecto secundario dentro de si la expresión o la expresión de **num\_threads** aparece.  
  
-   **captura** ejecutado dentro de una región paralela debe producir la ejecución al reanudar dentro de la extensión dinámica igual el bloque estructurado, y debe ser detectado por el mismo subproceso que produjo la excepción.  
  
-   Una sola cláusula de **num\_threads** puede aparecer en la directiva.  La expresión de **num\_threads** se evalúa fuera del contexto de la región paralela, y se debe evaluar como un valor de entero positivo.  
  
-   El orden de evaluación de las cláusulas de **If \[SQL2008\]** y de **num\_threads** no está especificado.  
  
## referencias cruzadas:  
  
-   **private**, **firstprivate**, **predeterminado**, **compartido**, **copyin**, y las cláusulas de **informe detallado** , vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.  
  
-   Variable de entorno**OMP\_NUM\_THREADS** , [sección 4,2](../../parallel/openmp/4-2-omp-num-threads.md) en la página 48.  
  
-   la función de biblioteca de**omp\_set\_dynamic** , vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.  
  
-   La variable de entorno**OMP\_DYNAMIC** , vea [sección 4,3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.  
  
-   la función de**omp\_set\_nested** , vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.  
  
-   La variable de entorno**OMP\_NESTED** , vea [sección 4,4](../Topic/4.4%20OMP_NESTED.md) en la página 49.  
  
-   la función de biblioteca de**omp\_set\_num\_threads** , vea [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.