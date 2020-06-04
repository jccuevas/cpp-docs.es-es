---
title: Contextos
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 9eaf21a3d65ae891a48657de9d3e7aff78ce12b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142190"
---
# <a name="contexts"></a>Contextos

En este documento se describe el rol de los contextos en el Runtime de simultaneidad. Un subproceso que se adjunta a un programador se conoce como *contexto de ejecución*o simplemente *contexto*. La función [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) y la clase Concurrency::[Context](../../parallel/concrt/reference/context-class.md) permiten controlar el comportamiento de los contextos. Utilice la función `wait` para suspender el contexto actual durante un tiempo especificado. Utilice la clase `Context` cuando necesite más control sobre cuándo los contextos se bloquean, desbloquean y producen, o Cuándo se desea sobresuscribir el contexto actual.

> [!TIP]
> Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

## <a name="the-wait-function"></a>La función wait

La función [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) produce de forma cooperativa la ejecución del contexto actual durante un número especificado de milisegundos. El motor en tiempo de ejecución utiliza el tiempo de Yield para realizar otras tareas. Una vez transcurrido el tiempo especificado, el tiempo de ejecución vuelve a programar el contexto para la ejecución. Por lo tanto, la función `wait` podría suspender el contexto actual más tiempo que el valor proporcionado para el parámetro `milliseconds`.

Al pasar 0 (cero) para el parámetro `milliseconds`, el tiempo de ejecución suspende el contexto actual hasta que todos los demás contextos activos tengan la oportunidad de realizar el trabajo. Esto le permite producir una tarea en todas las demás tareas activas.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo en el que se usa la función `wait` para producir el contexto actual y, por tanto, permitir que se ejecuten otros contextos, vea [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>La clase de contexto

La clase Concurrency::[Context](../../parallel/concrt/reference/context-class.md) proporciona una abstracción de programación para un contexto de ejecución y ofrece dos características importantes: la capacidad de bloquear, desbloquear y producir de forma cooperativa el contexto actual, y la capacidad de subsuscribir el contexto actual.

### <a name="cooperative-blocking"></a>Bloqueo cooperativo

La clase `Context` permite bloquear o ceder el contexto de ejecución actual. Bloquear o producir es útil cuando el contexto actual no puede continuar porque un recurso no está disponible.

El método [Concurrency:: context:: Block](reference/context-class.md#block) bloquea el contexto actual. Un contexto que está bloqueado produce sus recursos de procesamiento para que el motor en tiempo de ejecución pueda realizar otras tareas. El método [Concurrency:: context:: unblock](reference/context-class.md#unblock) desbloquea un contexto bloqueado. Se debe llamar al método `Context::Unblock` desde un contexto diferente al que llamó a `Context::Block`. El Runtime produce [Concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) si un contexto intenta desbloquearse.

Para bloquear y desbloquear un contexto de forma cooperativa, normalmente se llama a [Concurrency:: context:: CurrentContext](reference/context-class.md#currentcontext) para recuperar un puntero al objeto `Context` asociado al subproceso actual y guardar el resultado. A continuación, llame al método `Context::Block` para bloquear el contexto actual. Después, llame a `Context::Unblock` desde un contexto independiente para desbloquear el contexto bloqueado.

Debe hacer coincidir cada par de llamadas con `Context::Block` y `Context::Unblock`. El Runtime produce [Concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) cuando se llama a los métodos `Context::Block` o `Context::Unblock` consecutivamente sin una llamada coincidente al otro método. Sin embargo, no es necesario llamar a `Context::Block` antes de llamar a `Context::Unblock`. Por ejemplo, si un contexto llama a `Context::Unblock` antes de que otro contexto llame a `Context::Block` para el mismo contexto, ese contexto permanece desbloqueado.

El método [Concurrency:: context:: yield](reference/context-class.md#yield) produce la ejecución de modo que el tiempo de ejecución pueda realizar otras tareas y, a continuación, volver a programar el contexto para su ejecución. Cuando se llama al método `Context::Block`, el motor en tiempo de ejecución no vuelve a programar el contexto.

#### <a name="example"></a>Ejemplo

Para obtener un ejemplo en el que se usan los métodos `Context::Block`, `Context::Unblock`y `Context::Yield` para implementar una clase de semáforo cooperativa, vea [Cómo: usar la clase context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Suscripción excesiva

El programador predeterminado crea el mismo número de subprocesos que los subprocesos de hardware disponibles. Puede usar la *suscripción excesiva* para crear subprocesos adicionales para un subproceso de hardware determinado.

En el caso de las operaciones que requieren un uso intensivo de la informática, la sobresuscripción normalmente no escala porque introduce una sobrecarga adicional. Sin embargo, para las tareas que tienen una gran cantidad de latencia (por ejemplo, la lectura de datos del disco o de una conexión de red), la sobresuscripción puede mejorar la eficacia global de algunas aplicaciones.

> [!NOTE]
> Habilitar la suscripción excesiva solo desde un subproceso creado por el Runtime de simultaneidad. La sobresuscripción no tiene ningún efecto cuando se llama desde un subproceso que no se creó en tiempo de ejecución (incluido el subproceso principal).

Para habilitar la sobresuscripción en el contexto actual, llame al método [Concurrency:: context:: subsubscribe](reference/context-class.md#oversubscribe) con el parámetro `_BeginOversubscription` establecido en **true**. Al habilitar la suscripción excesiva en un subproceso creado por el Runtime de simultaneidad, hace que el tiempo de ejecución cree un subproceso adicional. Después de todas las tareas que requieren una suscripción excesiva, llame a `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en **false**.

Puede habilitar la sobresuscripción varias veces desde el contexto actual, pero debe deshabilitarlo el mismo número de veces que lo habilita. La sobresuscripción también puede estar anidada; es decir, una tarea creada por otra tarea que usa la sobresuscripción también puede sobrescribir su contexto. Sin embargo, si una tarea anidada y su elemento primario pertenecen al mismo contexto, solo la llamada externa a `Context::Oversubscribe` provoca la creación de un subproceso adicional.

> [!NOTE]
> El Runtime produce [Concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) si la sobresuscripción está deshabilitada antes de habilitarla.

###### <a name="example"></a>Ejemplo

Para obtener un ejemplo en el que se usa la sobresuscripción para desplazar la latencia que se produce al leer datos de una conexión de red, consulte [Cómo: usar la sobresuscripción a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Consulte también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Procedimiento para usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Procedimiento para usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
