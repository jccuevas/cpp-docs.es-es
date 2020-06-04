---
title: 'Cómo: Administrar una instancia del programador'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141723"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Cómo: Administrar una instancia del programador

Las instancias del Programador permiten asociar directivas de programación concretas con varios tipos de cargas de trabajo. Este tema contiene dos ejemplos básicos que muestran cómo crear y administrar una instancia del programador.

En los ejemplos se crean programadores que usan las directivas del programador predeterminado. Para obtener un ejemplo en el que se crea un programador que usa una directiva personalizada, vea [Cómo: especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>Para administrar una instancia del programador en su aplicación

1. Cree un objeto [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) que contenga los valores de directiva que va a usar el programador.

1. Llame al método [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) o al método [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) para crear una instancia del programador.

   Si usa el método `Scheduler::Create`, llame al método [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) cuando necesite asociar el programador al contexto actual.

1. Llame a la función [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) para crear un identificador de un objeto de evento de restablecimiento automático no señalado.

1. Pase el identificador al objeto de evento que acaba de crear en el método [Concurrency:: CurrentScheduler:: RegisterShutdownEvent (](reference/currentscheduler-class.md#registershutdownevent) o el método [Concurrency:: Scheduler:: RegisterShutdownEvent (](reference/scheduler-class.md#registershutdownevent) . De esta forma se registra el evento que se debe establecer cuando se destruya el programador.

1. Realice las tareas que desea que programe el programador actual.

1. Llame al método [Concurrency:: CurrentScheduler::D Etach](reference/currentscheduler-class.md#detach) para desasociar el programador actual y restaurar el programador anterior como el actual.

   Si usa el método `Scheduler::Create`, llame al método [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) para reducir el recuento de referencias del objeto `Scheduler`.

1. Pase el identificador al evento a la función [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) para esperar a que se cierre el programador.

1. Llame a la función [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) para cerrar el identificador del objeto de evento.

## <a name="example"></a>Ejemplo

En el siguiente código se muestran dos maneras de administrar una instancia del programador. En cada ejemplo se usa primero el programador predeterminado para realizar una tarea que imprima el identificador único del programador actual. A continuación, se usa una instancia del programador para realizar la misma tarea de nuevo. Finalmente, en cada ejemplo se restaura el programador predeterminado como el actual y se realiza la tarea una vez más.

En el primer ejemplo se usa la clase [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para crear una instancia de Scheduler y asociarla con el contexto actual. En el segundo ejemplo se usa la clase [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) para realizar la misma tarea. Normalmente, la clase `CurrentScheduler` se usa con el programador actual. El segundo ejemplo, que usa la clase `Scheduler`, es útil si se desea controlar cuándo está asociado el programador al contexto actual o si se desea asociar programadores concretos a tareas concretas.

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

> **cl. exe/EHsc Scheduler-Instance. cpp**

## <a name="see-also"></a>Consulte también

[Instancias de Scheduler](../../parallel/concrt/scheduler-instances.md)<br/>
[Procedimiento para especificar directivas de Scheduler concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
