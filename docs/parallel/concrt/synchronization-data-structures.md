---
title: "Estructuras de datos de sincronización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dd1c47cad01e0324f8027593eb4933f70cd6191
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="synchronization-data-structures"></a>Estructuras de datos de sincronización
El Runtime de simultaneidad proporciona varias estructuras de datos que permiten sincronizar el acceso a los datos compartidos desde varios subprocesos. Estas estructuras de datos son útiles cuando se comparten los datos que modifican con poca frecuencia. Un objeto de sincronización, por ejemplo, una sección crítica, hace que otros subprocesos esperar hasta que el recurso compartido está disponible. Por lo tanto, si usa este tipo de objeto para sincronizar el acceso a datos que se utilizan con frecuencia, puede perder la escalabilidad de la aplicación. El [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) proporciona el [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) (clase), que le permite compartir un recurso entre varios subprocesos o tareas sin la necesidad de sincronización. Para obtener más información sobre la `combinable` de clases, consulte [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="top"></a> Secciones  
 En este tema se describe los siguientes tipos de bloques de mensajes asincrónicos en detalle:  
  
-   [critical_section)](#critical_section)  
  
-   [reader_writer_lock)](#reader_writer_lock)  
  
-   [scoped_lock y scoped_lock_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a>critical_section)  
 El [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) clase representa un objeto cooperativo de exclusión mutua que cede a otras tareas en lugar de adelantarse a ellas. Las secciones críticas son útiles cuando varios subprocesos requieren exclusivo acceso de lectura y escritura a los datos compartidos.  

 La `critical_section` clase no es reentrante. El [concurrency::critical_section::lock](reference/critical-section-class.md#lock) método produce una excepción de tipo [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) si es llamado por el subproceso que ya posee el bloqueo.  


  
### <a name="methods-and-features"></a>Métodos y características  
 La tabla siguiente muestran los métodos importantes que se definen mediante la `critical_section` clase.  
  
|Método|Descripción|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|Adquiere la sección crítica. Los bloques de contexto que realiza la llamada hasta que adquiere el bloqueo.|  
|[try_lock](reference/critical-section-class.md#try_lock)|Intenta adquirir la sección crítica, pero no se bloquea.|  
|[unlock](reference/critical-section-class.md#unlock)|Libera la sección crítica.|  
  
 [[Arriba](#top)]  
  
##  <a name="reader_writer_lock"></a>reader_writer_lock)  
 El [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) clase proporciona las operaciones de lectura/escritura de subprocesos a los datos compartidos. Usar bloqueos de lector/escritor cuando varios subprocesos requieren acceso de lectura simultánea a un recurso compartido pero apenas escriben en dicho recurso compartido. Esta clase proporciona solo un subproceso tenga acceso de escritura a un objeto en cualquier momento.  
  
 El `reader_writer_lock` clase puede realizar mejor que la `critical_section` clase porque un `critical_section` objeto adquiere acceso exclusivo a un recurso compartido, lo que impide el acceso de lectura simultáneo.  
  
 Al igual que el `critical_section` (clase), el `reader_writer_lock` clase representa un objeto cooperativo de exclusión mutua que cede a otras tareas en lugar de adelantarse a ellas.  
  
 Cuando un subproceso que debe escribir en un recurso compartido adquiere un bloqueo de lectura/escritura, otros subprocesos que también deben tener acceso a los recursos se bloquean hasta que el sistema de escritura libera el bloqueo. El `reader_writer_lock` clase es un ejemplo de un *preferencia de escritura* bloqueo, que es un bloqueo que desbloquea de escritura en espera antes de desbloquear los lectores en espera.  
  
 Al igual que el `critical_section` (clase), el `reader_writer_lock` clase no es reentrante. El [concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) y [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) métodos lanzan una excepción de tipo `improper_lock` si se llama a un subproceso que ya posee el bloqueo.  


  
> [!NOTE]
>  Dado que la `reader_writer_lock` clase es no reentrante, no se puede actualizar un bloqueo de solo lectura a un bloqueo de lector/escritor o degradar un bloqueo de lector/escritor a un bloqueo de solo lectura. Realizar alguna de estas operaciones, produce un comportamiento no especificado.  
  
### <a name="methods-and-features"></a>Métodos y características  
 La tabla siguiente muestran los métodos importantes que se definen mediante la `reader_writer_lock` clase.  
  
|Método|Descripción|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|Adquiere el acceso de lectura/escritura al bloqueo.|  
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Intenta adquirir acceso de lectura/escritura al bloqueo, pero no se bloquea.|  
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Adquiere el acceso de solo lectura al bloqueo.|  
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Intenta adquirir acceso de solo lectura al bloqueo, pero no se bloquea.|  
|[unlock](reference/reader-writer-lock-class.md#unlock)|Libera el bloqueo.|  
  
 [[Arriba](#top)]  
  
##  <a name="scoped_lock"></a>scoped_lock y scoped_lock_read  
 El `critical_section` y `reader_writer_lock` clases proporcionan clases anidadas auxiliares que simplifican la forma de trabajar con objetos de exclusión mutua. Estas clases auxiliares se denominan *bloqueos con ámbito*.  
  
 El `critical_section` clase contiene la [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) clase. El constructor adquiere el acceso al proporcionado `critical_section` objeto; el destructor libera el acceso a dicho objeto. El `reader_writer_lock` clase contiene la [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) (clase), que es similar a `critical_section::scoped_lock`, excepto en que administra el acceso de escritura al proporcionado `reader_writer_lock` objeto. El `reader_writer_lock` clase también contiene el [concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) clase. Esta clase administra el acceso de lectura al proporcionado `reader_writer_lock` objeto.  

  
 Los bloqueos con ámbito ofrecen varias ventajas cuando se trabaja con `critical_section` y `reader_writer_lock` objetos manualmente. Normalmente, se asigna un bloqueo con ámbito en la pila. Un bloqueo con ámbito libera automáticamente el acceso a su objeto de exclusión mutua cuando se destruye; por lo tanto, no se desbloquea manualmente el objeto subyacente. Esto es útil cuando una función contiene varias `return` instrucciones. Los bloqueos con ámbito también pueden ayudarle a escribir código seguro ante excepciones. Cuando un `throw` instrucción hace que la pila se desenrede, se llama al destructor de cualquier bloqueo con ámbito activo y, por tanto, se libera siempre correctamente el objeto de exclusión mutua.  
  
> [!NOTE]
>  Cuando se usa el `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, y `reader_writer_lock::scoped_lock_read` las clases, no libere manualmente el acceso al objeto subyacente para la exclusión mutua. Esto puede colocar el tiempo de ejecución en un estado no válido.  
  
##  <a name="event"></a>evento  
 El [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) clase representa un objeto de sincronización cuyo estado puede ser señalado o no señalado. A diferencia de los objetos de sincronización, por ejemplo, secciones críticas, cuya finalidad es proteger el acceso a los datos compartidos, los eventos sincronizan el flujo de ejecución.  
  
 La `event` clase es útil cuando una tarea ha completado el trabajo de otra tarea. Por ejemplo, una tarea podría señalar a otra tarea que ha leído datos desde una conexión de red o desde un archivo.  
  
### <a name="methods-and-features"></a>Métodos y características  
 La tabla siguiente muestran algunos de los métodos importantes que se definen mediante la `event` clase.  
  
|Método|Descripción|  
|------------|-----------------|  
|[espera](reference/event-class.md#wait)|Espera a que se señale el evento.|  
|[set](reference/event-class.md#set)|Establece el evento en el estado señalado.|  
|[reset](reference/event-class.md#reset)|Establece el evento en el estado no señalado.|  
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Espera a que se señalen varios eventos.|  

  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que muestra cómo utilizar el `event` de clases, consulte [comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Arriba](#top)]  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Comparación de estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 Se compara el comportamiento de las estructuras de datos de sincronización a las proporcionadas por la API de Windows.  
  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)  
 Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a los temas relacionados.

