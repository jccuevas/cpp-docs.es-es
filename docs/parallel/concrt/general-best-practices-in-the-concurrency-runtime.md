---
title: "Procedimientos recomendados generales con el Runtime de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Runtime de simultaneidad, procedimientos recomendados generales"
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedimientos recomendados generales con el Runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describen los procedimientos recomendados que se aplican a varias áreas del runtime de simultaneidad.  
  
##  <a name="top"></a> Secciones  
 Este documento contiene las siguientes secciones:  
  
-   [Usar las construcciones cooperativas de sincronización cuando sea posible](#synchronization)  
  
-   [Evitar las tareas largas que no producen resultados](#yield)  
  
-   [Usar la sobresuscripción para desplazar las operaciones que se bloquean o tienen alta latencia](#oversubscription)  
  
-   [Usar las funciones de administración de memoria simultáneas cuando sea posible](#memory)  
  
-   [Usar RAII para administrar la duración de los objetos de simultaneidad](#raii)  
  
-   [No crear objetos de simultaneidad en el ámbito global](#global-scope)  
  
-   [No usar objetos de simultaneidad en segmentos de datos compartidos](#shared-data)  
  
##  <a name="synchronization"></a> Usar las construcciones cooperativas de sincronización cuando sea posible  
 El runtime de simultaneidad proporciona muchas construcciones seguras para simultaneidad que no requieren un objeto de sincronización externo.  Por ejemplo, la clase [concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) proporciona operaciones de anexación y de acceso a elementos seguras para simultaneidad.  Sin embargo, para los casos en que se requiere acceso exclusivo a un recurso, el runtime proporciona las clases [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) y [concurrency::event](../../parallel/concrt/reference/event-class.md).  Estos tipos se comportan de forma cooperativa; por consiguiente, el programador de tareas puede reasignar los recursos de procesamiento a otro contexto mientras la primera tarea espera los datos.  Cuando sea posible, use estos tipos de sincronización en lugar de otros mecanismos de sincronización, como los proporcionados por la API de Windows, que no se comportan de manera cooperativa.  Para obtener más información sobre estos tipos de sincronización y un ejemplo de código, vea [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md) y [Comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="yield"></a> Evitar las tareas largas que no producen resultados  
 Dado que el programador de tareas se comporta de forma cooperativa, no es ecuánime entre las tareas.  Por consiguiente, una tarea puede evitar que se inicien otras tareas.  Aunque esto es aceptable en algunos casos, en otros puede producir un interbloqueo o un colapso.  
  
 En el siguiente ejemplo se realizan más tareas que el número de recursos de procesamiento asignados.  La primera tarea no produce resultados en el programador de tareas y, por consiguiente, la segunda tarea no se inicia hasta que finaliza la primera tarea.  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  
 Hay varias maneras de habilitar la cooperación entre las dos tareas.  Una consiste en producir ocasionalmente resultados de una tarea de ejecución prolongada en el programador de tareas.  En el ejemplo siguiente se modifica la función `task` para llamar al método [concurrency::Context::Yield](../Topic/Context::Yield%20Method.md), que realiza una ejecución en el programador de tareas, a fin de que se pueda ejecutar otra tarea.  
  
 [!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_2.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **1: 250000000**  
**2: 250000000**  
**1: 500000000**  
**2: 500000000**  
**1: 750000000**  
**2: 750000000**  
**1: 1000000000**  
**2: 1000000000** El método `Context::Yield` produce solo otro subproceso activo en el programador al que pertenece el subproceso actual, una tarea ligera u otro subproceso del sistema operativo.  Este método no produce resultados para un trabajo que está programado para ejecutarse en un objeto [concurrency::task\_group](../Topic/task_group%20Class.md) o [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md), pero que no se ha iniciado todavía.  
  
 Hay otras maneras de habilitar la cooperación entre las tareas de ejecución prolongada.  Puede dividir una tarea larga en otras más pequeñas.  También puede habilitar la sobresuscripción durante una tarea larga.  La sobresuscripción le permite crear más subprocesos que el número de subprocesos de hardware disponibles.  La sobresuscripción es especialmente útil cuando una tarea larga contiene mucha latencia, por ejemplo, al leer datos del disco o de una conexión de red.  Para obtener más información sobre las tareas ligeras y la sobresuscripción, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="oversubscription"></a> Usar la sobresuscripción para desplazar las operaciones que se bloquean o tienen alta latencia  
 El runtime de simultaneidad proporciona tipos primitivos de sincronización, como [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md), que permiten que las tareas se bloqueen de forma cooperativa y produzcan resultados entre sí.  Cuando una tarea se bloquea de forma cooperativa o produce resultados, el programador de tareas puede reasignar los recursos de procesamiento a otro contexto mientras la primera tarea espera los datos.  
  
 Hay casos en los que no se puede usar el mecanismo de bloqueo cooperativo que el runtime de simultaneidad proporciona.  Por ejemplo, una biblioteca externa que usa podría emplear un mecanismos de sincronización diferente.  Otro ejemplo es el caso en el que realiza una operación que podría tener mucha latencia, por ejemplo, cuando se usa la función de la API de Windows `ReadFile` para leer datos de una conexión de red.  En estos casos, la sobresuscripción puede permitir que otras tareas se ejecuten cuando otra tarea está inactiva.  La sobresuscripción le permite crear más subprocesos que el número de subprocesos de hardware disponibles.  
  
 Considere la función siguiente, `download`, que descarga el archivo en la dirección URL dada.  En este ejemplo se usa el método [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) para aumentar temporalmente el número de subprocesos activos.  
  
 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 Dado que la función `GetHttpFile` realiza una operación potencialmente latente, la sobresuscripción puede permitir que otras tareas se ejecuten mientras la tarea actual espera los datos.  Para obtener la versión completa de este ejemplo, vea [Cómo: Usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="memory"></a> Usar las funciones de administración de memoria simultáneas cuando sea posible  
 Use las funciones de administración de memoria, [concurrency::Alloc](../Topic/Alloc%20Function.md) y [concurrency::Free](../Topic/Free%20Function.md), cuando tenga tareas específicas que asignen a menudo objetos pequeños con una duración relativamente corta.  El runtime de simultaneidad contiene una memoria caché independiente para cada subproceso en ejecución.  Las funciones `Alloc` y `Free` asignan y liberan memoria de estas memorias caché sin el uso de bloqueos ni barreras de memoria.  
  
 Para obtener más información sobre estas funciones de administración de memoria, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  Para obtener un ejemplo en el que se usan estas características, vea [Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="raii"></a> Usar RAII para administrar la duración de los objetos de simultaneidad  
 El runtime de simultaneidad usa el control de excepciones para implementar características como la cancelación.  Por consiguiente, escriba el código seguro para excepciones cuando se llama al runtime o a otra biblioteca que llama al runtime.  
  
 El modelo *Resource Acquisition Is Initialization* \(RAII\) –que viene a significar que la adquisición de un recurso es su inicialización– es una forma de administrar con seguridad la duración de un objeto de simultaneidad en un ámbito determinado.  Bajo el modelo RAII, se asigna una estructura de datos en la pila.  Esa estructura de datos se inicializa o adquiere un recurso cuando se crea, y destruye o libera ese recurso cuando se destruye la estructura de datos.  El modelo RAII garantiza que se llama al destructor antes de que el ámbito de inclusión salga.  Este modelo resulta útil cuando una función contiene varias instrucciones `return`.  Este modelo también le ayuda a escribir código seguro para excepciones.  Cuando una instrucción `throw` hace que la pila se desenrede, se llama al destructor del objeto RAII; por consiguiente, el recurso siempre se elimina o se libera correctamente.  
  
 El runtime define varias clases que usan el patrón RAII, por ejemplo, [concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) y [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md).  Estas clases auxiliares se denominan *bloqueos con ámbito*.  Estas clases proporcionan varias ventajas al trabajar con objetos [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) o [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md).  El constructor de estas clases adquiere el acceso al objeto `critical_section` o `reader_writer_lock` proporcionado; el destructor libera el acceso a ese objeto.  Dado que un bloqueo con ámbito libera automáticamente el acceso a su objeto de exclusión mutua cuando se destruye; por consiguiente, no se desbloquea manualmente el objeto subyacente.  
  
 Considere la siguiente clase, `account`, que se define mediante una biblioteca externa y, por consiguiente, no se puede modificar.  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 En el siguiente ejemplo se realizan varias transacciones en un objeto `account` en paralelo.  En el ejemplo se usa un objeto `critical_section` para sincronizar el acceso al objeto `account` porque la clase `account` no es segura para simultaneidad.  Cada operación paralela usa un objeto `critical_section::scoped_lock` para garantizar que el objeto `critical_section` se desbloquea cuando la operación se realiza correctamente o tiene errores.  Cuando el saldo de cuenta es negativo, la operación `withdraw` produce un error e inicia una excepción.  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo:  
  
  **Balance before deposit: 1924**  
**Balance after deposit: 2924**  
**Balance before withdrawal: 2924**  
**Balance after withdrawal: \-76**  
**Balance before withdrawal: \-76**  
**Error details:**  
 **negative balance: \-76** Para obtener ejemplos adicionales en los que se usa el modelo RAII para administrar la duración de los objetos de simultaneidad, vea [Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [Cómo: Usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md) y [Cómo: Usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="global-scope"></a> No crear objetos de simultaneidad en el ámbito global  
 Cuando se crea un objeto de simultaneidad en el ámbito global, pueden surgir problemas en la aplicación, como infracciones de acceso a la memoria o interbloqueo.  
  
 Por ejemplo, cuando se crea un objeto de runtime de simultaneidad, el runtime crea un programador predeterminado para el usuario si aún no se había creado.  Un objeto en tiempo de ejecución creado durante la construcción de objetos globales provocará que el runtime cree este programador predeterminado.  Sin embargo, este proceso utiliza un bloqueo interno, lo que puede interferir con la inicialización de otros objetos que admiten la infraestructura del runtime de simultaneidad.  Otro objeto de la infraestructura que aún no se haya inicializado podría requerir este bloqueo interno y provocar, por tanto, un interbloqueo en la aplicación.  
  
 En el ejemplo siguiente se muestra la creación de un objeto [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) global.  Este patrón no se aplica solo a la clase `Scheduler`, sino también al resto de tipos que proporciona el runtime de simultaneidad.  Es recomendable que no siga este patrón, ya que puede provocar un comportamiento inesperado en la aplicación.  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 Para obtener ejemplos de la forma correcta de crear los objetos `Scheduler`, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="shared-data"></a> No usar objetos de simultaneidad en segmentos de datos compartidos  
 El runtime de simultaneidad no admite el uso de objetos de simultaneidad en una sección de datos compartidos, por ejemplo, una sección de datos que se crea mediante la directiva [data\_seg](../../preprocessor/data-seg.md) `#pragma`.  Un objeto de simultaneidad que se comparte entre los límites del proceso puede colocar el runtime en un estado incoherente o no válido.  
  
 \[[Arriba](#top)\]  
  
## Vea también  
 [Procedimientos recomendados del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)   
 [Comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [Cómo: Usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [Cómo: Usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Procedimientos recomendados en la biblioteca de agentes asincrónicos](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)