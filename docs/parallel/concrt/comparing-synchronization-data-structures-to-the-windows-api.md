---
title: Comparar estructuras de datos de sincronización con la API de Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff827c326f331acae4d16381856ad4df01550524
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447055"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Comparar estructuras de datos de sincronización con la API de Windows

En este tema se compara el comportamiento de las estructuras de datos de sincronización que proporciona el Runtime de simultaneidad con las que proporciona la API de Windows.

Las estructuras de datos de sincronización que proporcionan el Runtime de simultaneidad siguen el *cooperativa de modelo de subprocesos*. En este modelo, las primitivas de sincronización ceden explícitamente sus recursos de procesamiento a otros subprocesos. Esto difiere de la *preferente de modelo de subprocesos*, donde los recursos de procesamiento se transfieren a otros subprocesos por el sistema operativo o el programador de control.

## <a name="criticalsection"></a>critical_section

El [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) es similar a la Windows `CRITICAL_SECTION` estructura porque puede usarse únicamente por los subprocesos de un proceso. Para obtener más información acerca de las secciones críticas en la API de Windows, consulte [objetos de sección crítica](/windows/desktop/Sync/critical-section-objects).

## <a name="readerwriterlock"></a>reader_writer_lock

El [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) es similar a bloqueos finos de lector/escritor (SRW) de Windows. En la tabla siguiente se explican las similitudes y las diferencias.

|Característica|`reader_writer_lock`|Bloqueo SRW|
|-------------|--------------------------|--------------|
|No reentrante|Sí|Sí|
|Puede promover un lector a un escritor (compatibilidad de actualización)|No|No|
|Puede degradar un escritor a un lector (compatibilidad de degradación)|No|No|
|Bloqueo de preferencia de escritura|Sí|No|
|Acceso FIFO a escritores|Sí|No|

Para obtener más información sobre los bloqueos SRW, vea [bloqueos finos de lector/escritor (SRW)](https://msdn.microsoft.com/library/windows/desktop/aa904937) en Platform SDK.

## <a name="event"></a>evento

El [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) es similar a un evento de restablecimiento manual sin nombre, de Windows. Sin embargo, un objeto `event` se comporta de forma cooperativa, en tanto que un evento de Windows se comporta con preferencia. Para obtener más información acerca de los eventos de Windows, consulte [objetos de evento](/windows/desktop/Sync/event-objects).

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

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

Para obtener más información acerca de las tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Vea también

[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)
