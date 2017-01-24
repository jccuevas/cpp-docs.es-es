---
title: "Estructuras de datos de sincronizaci&#243;n | Microsoft Docs"
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
helpviewer_keywords: 
  - "estructuras de datos de sincronización"
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: 26
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estructuras de datos de sincronizaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Runtime de simultaneidad proporciona varias estructuras de datos que permiten sincronizar el acceso a los datos compartidos de varios subprocesos.  Estas estructuras de datos son útiles en el caso de disponer de datos compartidos que apenas se modifican.  Un objeto de sincronización, como una sección crítica, hace que otros subprocesos esperen hasta que esté disponible el recurso compartido.  Por consiguiente, si se utiliza este tipo de objeto para sincronizar el acceso a datos de uso frecuente, es posible que la aplicación pierda escalabilidad.  [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) proporciona la clase de [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) , que permite compartir un recurso entre varios subprocesos o tareas sin necesidad de sincronización.  Para obtener más información sobre la clase `combinable`, vea [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="top"></a> Secciones  
 En este tema, se describen detalladamente los siguientes tipos de bloques de mensajes asincrónicos:  
  
-   [critical\_section](#critical_section)  
  
-   [reader\_writer\_lock](#reader_writer_lock)  
  
-   [scoped\_lock y scoped\_lock\_read](#scoped_lock)  
  
-   [evento](#event)  
  
##  <a name="critical_section"></a> critical\_section  
 La clase de [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) representa un objeto cooperativo de exclusión mutua que cede ante otras tareas en lugar de adelantarse a ellas.  Las secciones críticas son útiles cuando varios subprocesos requieren acceso exclusivo de lectura y escritura a los datos compartidos.  
  
 La clase `critical_section` es no reentrante.  El método de [concurrency::critical\_section::lock](../Topic/critical_section::lock%20Method.md) produce una excepción de [concurrency::improper\_lock](../../parallel/concrt/reference/improper-lock-class.md) tipo si llama el subproceso que ya posee el bloqueo.  
  
### Métodos y características  
 En la tabla siguiente se muestran los métodos importantes definidos por la clase `critical_section`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[bloquear](../Topic/critical_section::lock%20Method.md)|Adquiere la sección crítica.  El contexto de la llamada se bloquea hasta que adquiere el bloqueo.|  
|[try\_lock](../Topic/critical_section::try_lock%20Method.md)|Intenta adquirir la sección crítica, pero no se bloquea.|  
|[unlock](../Topic/critical_section::unlock%20Method.md)|Libera la sección crítica.|  
  
 \[[Arriba](#top)\]  
  
##  <a name="reader_writer_lock"></a> reader\_writer\_lock  
 La clase de [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) proporciona operaciones de lectura y escritura seguro para subprocesos a los datos compartidos.  Utilice bloqueos de lectura o escritura cuando varios subprocesos requieren acceso de lectura simultáneo a un recurso compartido pero apenas escriben en dicho recurso.  Esta clase solo proporciona acceso de escritura a un objeto a la vez.  
  
 La clase `reader_writer_lock` tiene mejor rendimiento que la clase `critical_section` porque un objeto `critical_section` adquiere acceso exclusivo a un recurso compartido, lo que evita el acceso de lectura simultáneo.  
  
 Al igual que la clase `critical_section`, la clase `reader_writer_lock` representa un objeto cooperativo de exclusión mutua que cede ante otras tareas en lugar de adelantarse a ellas.  
  
 Cuando un subproceso que tiene que escribir en un recurso compartido adquiere un bloqueo de lectura o escritura, se bloquean otros subprocesos que también tienen que obtener acceso al recurso hasta que el sistema de escritura libera el bloqueo.  La clase `reader_writer_lock` es un ejemplo de un bloqueo de *preferencia de escritura*, que desbloquea los sistemas de escritura en espera antes de desbloquear los lectores en espera.  
  
 Al igual que la clase `critical_section`, la clase `reader_writer_lock` no es reentrante.  Los métodos de [concurrency::reader\_writer\_lock::lock](../Topic/reader_writer_lock::lock%20Method.md) y de [concurrency::reader\_writer\_lock::lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md) producen una excepción de `improper_lock` tipo si llama un subproceso que ya posee el bloqueo.  
  
> [!NOTE]
>  Dado que la clase `reader_writer_lock` no es una clase reentrante, un bloqueo de solo lectura no se puede actualizar a un bloqueo de lectura o escritura ni un bloqueo de lectura o escritura se puede degradar a un bloqueo de solo lectura.  Si se realiza alguna de estas operaciones, se produce un comportamiento inesperado.  
  
### Métodos y características  
 En la tabla siguiente se muestran los métodos importantes definidos por la clase `reader_writer_lock`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[bloquear](../Topic/reader_writer_lock::lock%20Method.md)|Adquiere acceso de lectura y escritura al bloqueo.|  
|[try\_lock](../Topic/reader_writer_lock::try_lock%20Method.md)|Intenta adquirir acceso de lectura y escritura al bloqueo, pero no se bloquea.|  
|[lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md)|Adquiere acceso de solo lectura al bloqueo.|  
|[try\_lock\_read](../Topic/reader_writer_lock::try_lock_read%20Method.md)|Intenta adquirir acceso de solo lectura al bloqueo, pero no se bloquea.|  
|[unlock](../Topic/reader_writer_lock::unlock%20Method.md)|Libera el bloqueo.|  
  
 \[[Arriba](#top)\]  
  
##  <a name="scoped_lock"></a> scoped\_lock y scoped\_lock\_read  
 Las clases `reader_writer_lock` y `critical_section` proporcionan clases auxiliares anidadas que simplifican la forma en que se usan los objetos de exclusión mutua.  Estas clases auxiliares se denominan *bloqueos con ámbito*.  
  
 La clase de `critical_section` contiene la clase de [concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) .  El constructor adquiere acceso al objeto `critical_section` proporcionado; el destructor libera el acceso a dicho objeto.  La clase de `reader_writer_lock` contiene la clase de [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md) , similar a `critical_section::scoped_lock`, salvo que administra el acceso de escritura al objeto proporcionado de `reader_writer_lock` .  La clase de `reader_writer_lock` también contiene la clase de [concurrency::reader\_writer\_lock::scoped\_lock\_read](../Topic/reader_writer_lock::scoped_lock_read%20Class.md) .  Esta clase administra el acceso de lectura al objeto `reader_writer_lock` proporcionado.  
  
 Los bloqueos con ámbito ofrecen varias ventajas cuando se usan los objetos `reader_writer_lock` y `critical_section` manualmente.  Normalmente, se asigna un bloqueo con ámbito en la pila.  Un bloqueo con ámbito libera automáticamente el acceso a su objeto de exclusión mutua cuando se destruye; por consiguiente, no se desbloquea manualmente el objeto subyacente.  Esto resulta útil cuando una función contiene varias instrucciones `return`.  Los bloqueos con ámbito también pueden ayudar a escribir código seguro ante excepciones.  Cuando una instrucción `throw` hace que se desenrede la pila, se invoca el destructor de cualquier bloqueo con ámbito activo, por lo que se libera siempre correctamente el objeto de exclusión mutua.  
  
> [!NOTE]
>  Cuando use las clases `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock_read` y `reader_writer_lock::scoped_lock`, no libere manualmente el acceso al objeto de exclusión mutua subyacente.  De ese modo, es posible que el runtime pase a un estado no válido.  
  
##  <a name="event"></a> evento  
 La clase de [concurrency::event](../../parallel/concrt/reference/event-class.md) representa un objeto de sincronización cuyo estado puede ser señalado o no ser señalado.  A diferencia de los objetos de sincronización, cuyo propósito es proteger el acceso a los datos compartidos \(por ejemplo, las secciones críticas\), los eventos sincronizan el flujo de ejecución.  
  
 La clase `event` resulta útil cuando una tarea ha completado el trabajo de otra tarea.  Por ejemplo, una tarea podría señalar a otra tarea que ha leído datos de una conexión de red o de un archivo.  
  
### Métodos y características  
 En la tabla siguiente, se muestran varios de los métodos importantes definidos por la clase `event`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[wait](../Topic/event::wait%20Method.md)|Espera a que se señale el evento.|  
|[set](../Topic/event::set%20Method.md)|Establece el evento en el estado señalado.|  
|[reset](../Topic/event::reset%20Method.md)|Establece el evento en el estado no señalado.|  
|[wait\_for\_multiple](../Topic/event::wait_for_multiple%20Method.md)|Espera a que se señalen varios eventos.|  
  
### Ejemplo  
 Para obtener un ejemplo en el que se muestra cómo usar la clase `event`, vea [Comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 \[[Arriba](#top)\]  
  
## Secciones relacionadas  
 [Comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 Se compara el comportamiento de las estructuras de datos de sincronización con el de la API de Windows.  
  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)  
 Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a temas relacionados.