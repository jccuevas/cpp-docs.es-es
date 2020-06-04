---
title: Comparar estructuras de datos de sincronización con la API de Windows
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510598"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Comparar estructuras de datos de sincronización con la API de Windows

En este tema se compara el comportamiento de las estructuras de datos de sincronización que proporciona el Runtime de simultaneidad con las que proporciona la API de Windows.

Las estructuras de datos de sincronización que proporciona el Runtime de simultaneidad siguen el *modelo*de subprocesos cooperativo. En este modelo, las primitivas de sincronización ceden explícitamente sus recursos de procesamiento a otros subprocesos. Esto difiere del *modelo*de subprocesos preferente, donde los recursos de procesamiento se transfieren a otros subprocesos por parte del programador de control o del sistema operativo.

## <a name="critical_section"></a>critical_section

La clase [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) es similar a la `CRITICAL_SECTION` estructura de Windows porque solo la pueden usar los subprocesos de un proceso. Para obtener más información sobre las secciones críticas de la API de Windows, vea [objetos de sección crítica](/windows/win32/Sync/critical-section-objects).

## <a name="reader_writer_lock"></a>reader_writer_lock

La clase [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) es similar a los bloqueos de lector fino de Windows (SRW). En la tabla siguiente se explican las similitudes y las diferencias.

|Característica|`reader_writer_lock`|Bloqueo SRW|
|-------------|--------------------------|--------------|
|No reentrante|Sí|Sí|
|Puede promover un lector a un escritor (compatibilidad de actualización)|Sin|Sin|
|Puede degradar un escritor a un lector (compatibilidad de degradación)|Sin|Sin|
|Bloqueo de preferencia de escritura|Sí|Sin|
|Acceso FIFO a escritores|Sí|Sin|

Para obtener más información acerca de los bloqueos SRW, consulte bloqueos finos de [lector/escritor (SRW)](/windows/win32/sync/slim-reader-writer--srw--locks) en el SDK de la plataforma.

## <a name="event"></a>evento

La clase [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) es similar a un evento de restablecimiento manual sin nombre de Windows. Sin embargo, un objeto `event` se comporta de forma cooperativa, en tanto que un evento de Windows se comporta con preferencia. Para obtener más información sobre los eventos de Windows, vea [objetos de evento](/windows/win32/Sync/event-objects).

## <a name="example"></a>Ejemplo

### <a name="description"></a>DESCRIPCIÓN

Para comprender mejor la diferencia entre la clase de `event` y los eventos de Windows, considere el siguiente ejemplo. Este ejemplo permite que el programador cree dos tareas simultáneas a lo sumo y, a continuación, llama a dos funciones similares que utilizan la clase `event` y un evento de restablecimiento manual de Windows. Cada función crea en primer lugar varias tareas que esperan hasta que se señaliza un evento compartido. A continuación, cada función cede el paso a las tareas en ejecución y, después, señala el evento. Posteriormente, cada función espera por el evento señalado.

### <a name="code"></a>Código

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Comentarios

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

La clase `event` se comporta de forma cooperativa, por lo que el programador puede reasignar los recursos del procesamiento a otro contexto cuando un evento está esperando para entrar en el estado señalado. Así, la versión que utiliza la clase `event` realiza más trabajo. En la versión que utiliza los eventos de Windows, cada tarea de espera debe entrar en el estado señalado antes de que se inicie la tarea siguiente.

Para obtener más información sobre las tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Vea también

[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)
