---
title: Contextos | Documentos de Microsoft
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
ms.openlocfilehash: 9a8297c8a7a779140f6464f39491e73950ddaeeb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="contexts"></a>Contextos

Este documento describe el rol de los contextos en el Runtime de simultaneidad. Un subproceso que se adjunta a un programador se conoce como un *contexto de ejecución*, o simplemente *contexto*. El [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función y la simultaneidad::[Context (clase)](../../parallel/concrt/reference/context-class.md) le permiten controlar el comportamiento de contextos. Use la `wait` función para suspender el contexto actual durante un tiempo especificado. Use la `Context` clase cuando se necesita más control sobre cuándo contextos bloquean, desbloquean y producen o cuando desee suscribir en exceso el contexto actual.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
## <a name="the-wait-function"></a>La función de espera  

 El [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función cede la ejecución del contexto actual para un número especificado de milisegundos de manera cooperativa. El runtime usa el tiempo de rendimiento para realizar otras tareas. Una vez transcurrido el tiempo especificado, el runtime reprograma el contexto de ejecución. Por lo tanto, la `wait` función podría suspender el contexto actual supera el valor proporcionado para el `milliseconds` parámetro.  
  
 Pasar un valor 0 (cero) el `milliseconds` parámetro hace que el tiempo de ejecución suspender el contexto actual hasta que todos los demás contextos activas tienen la oportunidad de realizar el trabajo. Esto le permite ceder una tarea a todas las demás tareas activas.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa el `wait` función para ceder el contexto actual y, por tanto, permitir que otros contextos de ejecución, consulte [Cómo: utilizar grupos de programación para influyen en orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="the-context-class"></a>La clase de contexto  
 La simultaneidad::[Context (clase)](../../parallel/concrt/reference/context-class.md) proporciona una abstracción de programación para un contexto de ejecución y proporciona dos características importantes: la capacidad de bloquear, desbloquear y ceder el contexto actual de forma cooperativa y la capacidad suscribir en exceso el contexto actual.  
  
### <a name="cooperative-blocking"></a>El bloqueo cooperativo  
 La clase `Context` permite bloquear o ceder el contexto de ejecución actual. Bloquear o ceder es útil cuando el contexto actual no puede continuar porque un recurso no está disponible.  
  

 El [concurrency::Context::Block](reference/context-class.md#block) método bloquea el contexto actual. Un contexto que se bloquea cede sus recursos de procesamiento para que el runtime pueda realizar otras tareas. El [concurrency::Context::Unblock](reference/context-class.md#unblock) método desbloquea un contexto bloqueado. El `Context::Unblock` método se debe invocar desde un contexto diferente a la que llama `Context::Block`. El runtime produce [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) si un contexto intenta desbloquearse a sí mismo.  
  
 Para la forma cooperativa bloquear y desbloquear un contexto, se suele llamar a [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) para recuperar un puntero a la `Context` objeto que está asociado con el subproceso actual y guardar el resultado. A continuación, llame a la `Context::Block` método para bloquear el contexto actual. Después, llame a `Context::Unblock` desde un contexto independiente para desbloquear el contexto bloqueado.  
  
 Debe coincidir con cada par de llamadas a `Context::Block` y `Context::Unblock`. El runtime produce [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) cuando el `Context::Block` o `Context::Unblock` método se llama de forma consecutiva sin una llamada correspondiente al otro método. Sin embargo, no es necesario llamar a `Context::Block` antes de llamar a `Context::Unblock`. Por ejemplo, si llama a un contexto `Context::Unblock` antes de realizar otra llamada de contexto `Context::Block` para el mismo contexto, ese contexto permanece desbloqueado.  
  
 El [concurrency::Context::Yield](reference/context-class.md#yield) método genera la ejecución para que el tiempo de ejecución pueda realizar otras tareas y, a continuación, volver a programar el contexto de ejecución. Cuando se llama a la `Context::Block` (método), el runtime no reprograma el contexto.  

  
#### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa el `Context::Block`, `Context::Unblock`, y `Context::Yield` métodos para implementar una clase de semáforo cooperativa, vea [Cómo: usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
##### <a name="oversubscription"></a>Suscripción excesiva  
 El programador predeterminado crea el mismo número de subprocesos que hay subprocesos de hardware disponibles. Puede usar *suscripción excesiva* para crear subprocesos adicionales para un subproceso de hardware determinado.  
  
 Para operaciones intensivas, suscripción excesiva normalmente no se escala porque introduce una sobrecarga adicional. Sin embargo, para las tareas que tienen una gran cantidad de latencia, por ejemplo, leer datos desde el disco o de una conexión de red, suscripción excesiva puede mejorar la eficacia general de algunas aplicaciones.  
  
> [!NOTE]
>  Habilitar la sobresuscripción solo desde un subproceso creado por el Runtime de simultaneidad. Suscripción excesiva no tiene ningún efecto cuando se llama desde un subproceso que no se creó en tiempo de ejecución (incluido el subproceso principal).  
  
 Para habilitar la suscripción excesiva en el contexto actual, llame a la [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) método con el `_BeginOversubscription` parámetro establecido en `true`. Cuando se habilita la suscripción excesiva en un subproceso creado por el Runtime de simultaneidad, hace que el runtime cree un subproceso adicional. Después de todas las tareas que requieren la finalización de la suscripción excesiva, llame al método `Context::Oversubscribe` con el `_BeginOversubscription` parámetro establecido en `false`.  

  
 Puede habilitar la sobresuscripción varias veces desde el contexto actual, pero debe deshabilitar al mismo número de veces que habilitarlo. También se puede anidar la suscripción excesiva; es decir, una tarea que se crea por otra tarea que usa la suscripción excesiva también puede saturar su contexto. Sin embargo, si una tarea anidada y su elemento primario pertenecen al mismo contexto, solo la llamada exterior a `Context::Oversubscribe` hace que la creación de un subproceso adicional.  
  
> [!NOTE]
>  El runtime produce [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) si se deshabilita la suscripción excesiva antes de habilitarla.  
  
###### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa la suscripción excesiva para compensar la latencia que se produce al leer datos de una conexión de red, consulte [Cómo: usar la sobresuscripción a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [Cómo: usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Procedimiento para usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

