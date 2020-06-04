---
title: Estructuras de datos de sincronización
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 85dec6b003330a3560ae1dcc5c41b5e6d49f765e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142805"
---
# <a name="synchronization-data-structures"></a>Estructuras de datos de sincronización

El Runtime de simultaneidad proporciona varias estructuras de datos que permiten sincronizar el acceso a los datos compartidos desde varios subprocesos. Estas estructuras de datos son útiles cuando se comparten datos que se modifican con poca frecuencia. Un objeto de sincronización, por ejemplo, una sección crítica, hace que otros subprocesos esperen hasta que el recurso compartido esté disponible. Por lo tanto, si usa este tipo de objeto para sincronizar el acceso a los datos que se usan con frecuencia, puede perder la escalabilidad en la aplicación. La [biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) proporciona la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) , que permite compartir un recurso entre varios subprocesos o tareas sin necesidad de sincronización. Para obtener más información sobre la clase `combinable`, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="top"></a> Secciones

En este tema se describen los siguientes tipos de bloques de mensajes asincrónicos en detalle:

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock y scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a>critical_section

La clase [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) representa un objeto de exclusión mutua cooperativa que produce otras tareas en lugar de tener que adelantarlos. Las secciones críticas son útiles cuando varios subprocesos requieren acceso exclusivo de lectura y escritura a los datos compartidos.

La clase `critical_section` no es reentrante. El método [Concurrency:: critical_section:: Lock](reference/critical-section-class.md#lock) produce una excepción de tipo [Concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md) si lo llama el subproceso que ya posee el bloqueo.

### <a name="methods-and-features"></a>Métodos y características

En la tabla siguiente se muestran los métodos importantes definidos por la clase `critical_section`.

|Método|Descripción|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Adquiere la sección crítica. El contexto de llamada se bloquea hasta que adquiere el bloqueo.|
|[try_lock](reference/critical-section-class.md#try_lock)|Intenta adquirir la sección crítica, pero no se bloquea.|
|[unlock](reference/critical-section-class.md#unlock)|Libera la sección crítica.|

[[Arriba](#top)]

## <a name="reader_writer_lock"></a>reader_writer_lock

La clase [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) proporciona operaciones de lectura/escritura seguras para subprocesos a los datos compartidos. Use bloqueos de lectura/escritura cuando varios subprocesos requieran acceso de lectura simultáneo a un recurso compartido, pero raramente se escriban en ese recurso compartido. Esta clase proporciona a un solo subproceso el acceso de escritura a un objeto en cualquier momento.

La clase `reader_writer_lock` puede tener un rendimiento mejor que la clase `critical_section` porque un objeto `critical_section` adquiere acceso exclusivo a un recurso compartido, lo que impide el acceso de lectura simultáneo.

Al igual que la clase `critical_section`, la clase `reader_writer_lock` representa un objeto de exclusión mutua cooperativa que produce otras tareas en lugar de tener que adelantarlas.

Cuando un subproceso que debe escribir en un recurso compartido adquiere un bloqueo de lector/escritor, otros subprocesos que también deben tener acceso al recurso se bloquean hasta que el escritor libera el bloqueo. La clase `reader_writer_lock` es un ejemplo de un bloqueo de *preferencia de escritura* , que es un bloqueo que desbloquea los escritores en espera antes de desbloquear los lectores en espera.

Al igual que la clase `critical_section`, la clase `reader_writer_lock` no es reentrante. Los métodos [Concurrency:: reader_writer_lock:: Lock](reference/reader-writer-lock-class.md#lock) y [Concurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read) producen una excepción de tipo `improper_lock` si se llama por parte de un subproceso que ya posee el bloqueo.

> [!NOTE]
> Dado que la clase `reader_writer_lock` no es reentrante, no se puede actualizar un bloqueo de solo lectura a un bloqueo lector/escritor ni degradar un bloqueo de lector/escritor a un bloqueo de solo lectura. Al realizar cualquiera de estas operaciones, se produce un comportamiento no especificado.

### <a name="methods-and-features"></a>Métodos y características

En la tabla siguiente se muestran los métodos importantes definidos por la clase `reader_writer_lock`.

|Método|Descripción|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Adquiere acceso de lectura y escritura al bloqueo.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Intenta adquirir acceso de lectura y escritura al bloqueo, pero no se bloquea.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Adquiere acceso de solo lectura al bloqueo.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Intenta adquirir acceso de solo lectura al bloqueo, pero no se bloquea.|
|[unlock](reference/reader-writer-lock-class.md#unlock)|Libera el bloqueo.|

[[Arriba](#top)]

## <a name="scoped_lock"></a>scoped_lock y scoped_lock_read

Las clases `critical_section` y `reader_writer_lock` proporcionan clases auxiliares anidadas que simplifican la forma de trabajar con objetos de exclusión mutua. Estas clases auxiliares se conocen como *bloqueos de ámbito*.

La clase `critical_section` contiene la clase [Concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) . El constructor adquiere el acceso al objeto `critical_section` proporcionado; el destructor libera el acceso a ese objeto. La clase `reader_writer_lock` contiene la clase [Concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) , que se parece a `critical_section::scoped_lock`, con la salvedad de que administra el acceso de escritura al objeto `reader_writer_lock` proporcionado. La clase `reader_writer_lock` también contiene la clase [Concurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) . Esta clase administra el acceso de lectura al objeto de `reader_writer_lock` proporcionado.

Los bloqueos de ámbito proporcionan varias ventajas cuando se trabaja con objetos `critical_section` y `reader_writer_lock` de forma manual. Normalmente, se asigna un bloqueo con ámbito en la pila. Un bloqueo con ámbito libera automáticamente el acceso a su objeto de exclusión mutua cuando se destruye; por lo tanto, no se desbloquea manualmente el objeto subyacente. Esto resulta útil cuando una función contiene varias instrucciones `return`. Los bloqueos de ámbito también pueden ayudarle a escribir código seguro para excepciones. Cuando una instrucción `throw` hace que la pila se desenrede, se llama al destructor de cualquier bloqueo de ámbito activo y, por tanto, el objeto de exclusión mutua siempre se libera correctamente.

> [!NOTE]
> Cuando use las clases `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`y `reader_writer_lock::scoped_lock_read`, no libere manualmente el acceso al objeto de exclusión mutua subyacente. Esto puede poner el Runtime en un estado no válido.

## <a name="event"></a>ceso

La clase [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) representa un objeto de sincronización cuyo estado puede ser señalado o no señalizado. A diferencia de los objetos de sincronización, como las secciones críticas, cuyo propósito es proteger el acceso a los datos compartidos, los eventos sincronizan el flujo de ejecución.

La clase `event` es útil cuando una tarea ha completado el trabajo de otra tarea. Por ejemplo, una tarea puede indicar a otra tarea que ha leído datos de una conexión de red o de un archivo.

### <a name="methods-and-features"></a>Métodos y características

En la tabla siguiente se muestran algunos de los métodos importantes definidos por la clase `event`.

|Método|Descripción|
|------------|-----------------|
|[currir](reference/event-class.md#wait)|Espera a que se señale el evento.|
|[set](reference/event-class.md#set)|Establece el evento en el estado señalado.|
|[reset](reference/event-class.md#reset)|Establece el evento en el estado no señalado.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Espera a que se señalen varios eventos.|

### <a name="example"></a>Ejemplo

Para obtener un ejemplo que muestra cómo usar la clase `event`, consulte [comparar estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Arriba](#top)]

## <a name="related-sections"></a>Secciones relacionadas

[Comparación de estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Compara el comportamiento de las estructuras de datos de sincronización con los proporcionados por la API de Windows.

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)<br/>
Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a los temas relacionados.
