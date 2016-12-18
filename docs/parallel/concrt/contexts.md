---
title: "Contextos | Microsoft Docs"
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
  - "contextos [Runtime de simultaneidad]"
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contextos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este documento describe el rol de contextos en el Runtime de simultaneidad. Un subproceso que se adjunta a un programador se conoce como un *contexto de ejecución*, o simplemente *contexto*. El [Concurrency:: wait](../Topic/wait%20Function.md) función y la simultaneidad::[clase de contexto](../../parallel/concrt/reference/context-class.md) le permiten controlar el comportamiento de contextos. Utilice la `wait` función suspender el contexto actual durante un tiempo especificado. Utilice la `Context` clase cuando se necesita más control sobre cuándo contextos bloquearán, desbloquean y producen o cuando desee suscribir en exceso el contexto actual.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que empiece con el [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) Si está familiarizado con el Runtime de simultaneidad.  
  
## <a name="the-wait-function"></a>La función de espera  
 El [Concurrency:: wait](../Topic/wait%20Function.md) función cede la ejecución del contexto actual para un número especificado de milisegundos de manera cooperativa. El tiempo de ejecución utiliza el tiempo de rendimiento para realizar otras tareas. Una vez transcurrido el tiempo especificado, el tiempo de ejecución reprograma el contexto de ejecución. Por lo tanto, la `wait` función podría suspender el contexto actual supera el valor proporcionado para el `milliseconds` parámetro.  
  
 Pasar un valor 0 (cero) el `milliseconds` parámetro hace que el tiempo de ejecución suspender el contexto actual hasta que todos los demás contextos activos tienen la oportunidad de realizar el trabajo. Esto le permite ceder una tarea a todas las demás tareas activas.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que utiliza el `wait` funcione para ceder el contexto actual y, por tanto, permitir que otros contextos de ejecución, vea [Cómo: usar grupos de programación que influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="the-context-class"></a>La clase de contexto  
 La simultaneidad::[clase de contexto](../../parallel/concrt/reference/context-class.md) proporciona una abstracción de programación para un contexto de ejecución y ofrece dos características importantes: la capacidad de bloquear, desbloquear y ceder el contexto actual de forma cooperativa y la capacidad de suscribir en exceso el contexto actual.  
  
### <a name="cooperative-blocking"></a>Bloqueo cooperativo  
 La clase `Context` permite bloquear o ceder el contexto de ejecución actual. Bloquear o ceder es útil cuando el contexto actual no puede continuar porque un recurso no está disponible.  
  
 El [concurrency::Context::Block](../Topic/Context::Block%20Method.md) método bloquea el contexto actual. Un contexto que se bloquea cede sus recursos de procesamiento para que el runtime pueda realizar otras tareas. El [concurrency::Context::Unblock](../Topic/Context::Unblock%20Method.md) método desbloquea un contexto bloqueado. El `Context::Unblock` método debe llamarse desde un contexto diferente al que se llama `Context::Block`. El runtime produce [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) Si un contexto intenta desbloquearse.  
  
 Para colaboración bloquear y desbloquear un contexto, se suele llamar a [concurrency::Context::CurrentContext](../Topic/Context::CurrentContext%20Method.md) para recuperar un puntero a la `Context` objeto asociado con el subproceso actual y guardar el resultado. A continuación, llame el `Context::Block` para bloquear el contexto actual. Después, llame a `Context::Unblock` desde un contexto independiente para desbloquear el contexto bloqueado.  
  
 Debe coincidir con cada par de llamadas a `Context::Block` y `Context::Unblock`. El runtime produce [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) cuando el `Context::Block` o `Context::Unblock` se invoca consecutivamente sin una llamada correspondiente al otro método. Sin embargo, no es necesario llamar a `Context::Block` antes de llamar a `Context::Unblock`. Por ejemplo, si un contexto llama a `Context::Unblock` antes de otro contexto llame `Context::Block` para el mismo contexto, ese contexto permanece desbloqueado.  
  
 El [concurrency::Context::Yield](../Topic/Context::Yield%20Method.md) método genera la ejecución para que el tiempo de ejecución pueda realizar otras tareas y, a continuación, volver a programar el contexto de ejecución. Cuando se llama a la `Context::Block` (método), el runtime no reprograma el contexto.  
  
#### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que utiliza el `Context::Block`, `Context::Unblock`, y `Context::Yield` métodos para implementar una clase de semáforo cooperativa, vea [Cómo: usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
##### <a name="oversubscription"></a>Suscripción excesiva  
 El programador predeterminado crea el mismo número de subprocesos como subprocesos de hardware disponibles. Puede usar *sobresuscripción* para crear subprocesos adicionales para un subproceso de hardware determinado.  
  
 Para operaciones intensivas, suscripción excesiva normalmente no escala porque introduce sobrecarga adicional. Sin embargo, para las tareas que tienen una latencia elevada, por ejemplo, leer datos desde el disco o de una conexión de red, suscripción excesiva puede mejorar la eficacia general de algunas aplicaciones.  
  
> [!NOTE]
>  Habilitar la sobresuscripción sólo desde un subproceso creado por el Runtime de simultaneidad. Suscripción excesiva no tiene ningún efecto cuando se llama desde un subproceso que no se creó en tiempo de ejecución (incluido el subproceso principal).  
  
 Para habilitar la suscripción excesiva en el contexto actual, llame a la [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) método con el `_BeginOversubscription` establecido en `true`. Cuando se habilita la suscripción excesiva en un subproceso creado por el Runtime de simultaneidad, hace que el runtime cree un subproceso adicional. Después de todas las tareas que requieren la finalización de la suscripción excesiva, llame al método `Context::Oversubscribe` con el `_BeginOversubscription` establecido en `false`.  
  
 Puede habilitar la sobresuscripción varias veces desde el contexto actual, pero debe deshabilitar al mismo número de veces que habilitarlo. Suscripción excesiva también se puede anidar. es decir, una tarea que se crea otra tarea que usa la suscripción excesiva también puede saturar su contexto. Sin embargo, si una tarea anidada y su elemento primario pertenecen al mismo contexto, solo la más externa llamada a `Context::Oversubscribe` provoca la creación de un subproceso adicional.  
  
> [!NOTE]
>  El runtime produce [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) Si la suscripción excesiva se deshabilite antes de que está habilitado.  
  
###### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa la suscripción excesiva para compensar la latencia que se produce al leer datos de una conexión de red, vea [Cómo: usar la sobresuscripción a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [Cómo: usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Cómo: usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

