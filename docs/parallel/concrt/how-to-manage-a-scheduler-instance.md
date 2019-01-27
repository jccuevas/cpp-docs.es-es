---
title: Procedimiento Administrar una instancia del programador
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: d8e79f7c132abd8e43f661f4dc7c7bb758cb2a6d
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893995"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Procedimiento Administrar una instancia del programador

Las instancias del Programador permiten asociar directivas de programación concretas con varios tipos de cargas de trabajo. Este tema contiene dos ejemplos básicos que muestran cómo crear y administrar una instancia del programador.

En los ejemplos se crean programadores que usan las directivas del programador predeterminado. Para un ejemplo que crea un programador que usa una directiva personalizada, vea [Cómo: Especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Para administrar una instancia del programador en su aplicación

1. Crear un [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) valores de objeto que contiene la directiva para que debe usar el programador.

1. Llame a la [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) método o la [concurrency::Scheduler::Create](reference/scheduler-class.md#create) método para crear una instancia del programador.

   Si usas el `Scheduler::Create` método, llame a la [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) método cuando necesite asociar el programador con el contexto actual.

1. Llame a la [CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa) función para crear un identificador a un objeto de evento de restablecimiento automático no señalado.

1. Pasar el identificador al objeto de evento que acaba de crear para el [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) método o la [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) método. De esta forma se registra el evento que se debe establecer cuando se destruya el programador.

1. Realice las tareas que desea que programe el programador actual.

1. Llame a la [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) método para desasociar el programador actual y restaurar el programador anterior como el actual.

   Si usas el `Scheduler::Create` método, llame a la [concurrency::Scheduler::Release](reference/scheduler-class.md#release) método para reducir el recuento de referencias de la `Scheduler` objeto.

1. Pasar el identificador para el evento a la [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) función a esperar para que el programador se cierre.

1. Llame a la [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) función para cerrar el identificador del objeto de evento.

## <a name="example"></a>Ejemplo

En el siguiente código se muestran dos maneras de administrar una instancia del programador. En cada ejemplo se usa primero el programador predeterminado para realizar una tarea que imprima el identificador único del programador actual. A continuación, se usa una instancia del programador para realizar la misma tarea de nuevo. Finalmente, en cada ejemplo se restaura el programador predeterminado como el actual y se realiza la tarea una vez más.

El primer ejemplo utiliza la [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) clase para crear una instancia del programador y asociarla con el contexto actual. El segundo ejemplo usa el [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) clase para realizar la misma tarea. Normalmente, la clase `CurrentScheduler` se usa con el programador actual. El segundo ejemplo, que usa la clase `Scheduler`, es útil si se desea controlar cuándo está asociado el programador al contexto actual o si se desea asociar programadores concretos a tareas concretas.

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `scheduler-instance.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc scheduler-instance.cpp**

## <a name="see-also"></a>Vea también

[Instancias de Scheduler](../../parallel/concrt/scheduler-instances.md)<br/>
[Cómo: Especificar directivas de Scheduler concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

