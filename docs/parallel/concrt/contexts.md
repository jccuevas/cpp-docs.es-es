---
title: Contextos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7be66658c9452fa97c1971ae6719dccb06dbd836
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378226"
---
# <a name="contexts"></a>Contextos

Este documento describe el rol de los contextos en el Runtime de simultaneidad. Un subproceso que se adjunta a un programador se conoce como un *contexto de ejecución*, o simplemente *contexto*. El [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función y la simultaneidad::[clase de contexto](../../parallel/concrt/reference/context-class.md) le permiten controlar el comportamiento de contextos. Use el `wait` función para suspender el contexto actual durante un tiempo especificado. Use la `Context` clase cuando necesite más control sobre cuándo contextos bloquearán, desbloquean y producen o cuando desee saturar el contexto actual.

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

## <a name="the-wait-function"></a>La función espera

El [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función cede la ejecución del contexto actual para un número especificado de milisegundos de manera cooperativa. El tiempo de ejecución utiliza la hora de yield para realizar otras tareas. Una vez transcurrido el tiempo especificado, el runtime reprograma el contexto de ejecución. Por lo tanto, el `wait` función puede suspender el contexto actual supera el valor proporcionado para el `milliseconds` parámetro.

Pasar un valor 0 (cero) el `milliseconds` parámetro hace que el tiempo de ejecución suspender el contexto actual hasta que todos los demás contextos activos tienen la oportunidad de realizar el trabajo. Esto le permite producir una tarea en todas las otras tareas activas.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa el `wait` funcione para ceder el contexto actual y, por tanto, permite que otros contextos de ejecución, consulte [Cómo: utilizar grupos de programación para influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>La clase de contexto

La simultaneidad::[clase de contexto](../../parallel/concrt/reference/context-class.md) proporciona una abstracción de programación para un contexto de ejecución y ofrece dos características importantes: la capacidad de bloquear, desbloquear y ceder el contexto actual de forma cooperativa y la capacidad saturar el contexto actual.

### <a name="cooperative-blocking"></a>Bloqueo cooperativo

La clase `Context` permite bloquear o ceder el contexto de ejecución actual. Bloquear o ceder es útil cuando el contexto actual no puede continuar porque un recurso no está disponible.

El [Concurrency](reference/context-class.md#block) método bloquea el contexto actual. Un contexto que se bloquea cede sus recursos de procesamiento para que el runtime puede realizar otras tareas. El [concurrency::Context::Unblock](reference/context-class.md#unblock) método desbloquea un contexto bloqueado. El `Context::Unblock` método debe llamarse desde un contexto diferente a la que llama `Context::Block`. El runtime produce [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) si un contexto intenta desbloquearse a sí mismo.

Para forma cooperativa, bloquear y desbloquear un contexto, se suele llamar a [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) para recuperar un puntero a la `Context` objeto que está asociado con el subproceso actual y guarde el resultado. A continuación, llame a la `Context::Block` para bloquear el contexto actual. Después, llame a `Context::Unblock` desde un contexto independiente para desbloquear el contexto bloqueado.

Debe coincidir con cada par de llamadas a `Context::Block` y `Context::Unblock`. El runtime produce [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) cuando el `Context::Block` o `Context::Unblock` se llama al método consecutivamente sin una llamada al método de coincidencia. Sin embargo, no es necesario llamar a `Context::Block` antes de llamar a `Context::Unblock`. Por ejemplo, si llama un contexto `Context::Unblock` antes de realizar otra llamada contextual `Context::Block` para el mismo contexto, ese contexto permanece desbloqueado.

El [Concurrency](reference/context-class.md#yield) método proporciona una ejecución para que el tiempo de ejecución pueda realizar otras tareas y, a continuación, volver a programar el contexto de ejecución. Cuando se llama a la `Context::Block` método, el tiempo de ejecución no volver a programar el contexto.

#### <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa el `Context::Block`, `Context::Unblock`, y `Context::Yield` métodos para implementar una clase de semáforo cooperativa, vea [Cómo: usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Suscripción excesiva

El programador predeterminado crea el mismo número de subprocesos como subprocesos de hardware disponibles. Puede usar *la sobresuscripción* para crear subprocesos adicionales para un subproceso de hardware determinado.

Para operaciones intensivas, la suscripción excesiva normalmente no se escala porque introduce una sobrecarga adicional. Sin embargo, las tareas que tienen una latencia elevada, por ejemplo, leer los datos del disco o de una conexión de red, la suscripción excesiva puede mejorar la eficacia general de algunas aplicaciones.

> [!NOTE]
>  Habilitar la sobresuscripción solo desde un subproceso creado por el Runtime de simultaneidad. La suscripción excesiva no tiene ningún efecto cuando se llama desde un subproceso que no se creó con el tiempo de ejecución (incluido el subproceso principal).

Para habilitar la suscripción excesiva en el contexto actual, llame a la [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) método con el `_BeginOversubscription` parámetro establecido en `true`. Cuando se habilita la suscripción excesiva en un subproceso creado por el Runtime de simultaneidad, hace que el tiempo de ejecución crear un subproceso adicional. Después de todas las tareas que requieren la finalización de la suscripción excesiva, llame a `Context::Oversubscribe` con el `_BeginOversubscription` parámetro establecido en `false`.

Puede habilitar la sobresuscripción varias veces desde el contexto actual, pero debe deshabilitar al mismo número de veces que se habilita. También se puede anidar la sobresuscripción; es decir, una tarea que se crea mediante otra tarea que usa la suscripción excesiva también puede saturar su contexto. Sin embargo, si una tarea anidada y su elemento primario que pertenecen al mismo contexto, solo la más externa llamada a `Context::Oversubscribe` provoca la creación de un subproceso adicional.

> [!NOTE]
>  El runtime produce [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) si se deshabilita la suscripción excesiva para que se habilite.

###### <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa la suscripción excesiva para compensar la latencia que se produce al leer datos desde una conexión de red, consulte [Cómo: usar la suscripción excesiva a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Procedimiento para usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Procedimiento para usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

