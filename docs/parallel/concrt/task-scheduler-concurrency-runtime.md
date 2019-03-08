---
title: Programador de tareas (Runtime de simultaneidad)
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
ms.openlocfilehash: c5d37d320344d2ebf83be2c939f5a7372d4af306
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286814"
---
# <a name="task-scheduler-concurrency-runtime"></a>Programador de tareas (Runtime de simultaneidad)

Los temas de esta parte de la documentación describen las características relevantes del Programador de tareas de Runtime de simultaneidad. El Programador de tareas resulta útil para ajustar el rendimiento del código existente que usa Runtime de simultaneidad.

> [!IMPORTANT]
>  El programador de tareas no está disponible desde una aplicación de plataforma Universal de Windows (UWP). Para obtener más información, consulte [crear operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
>  En Visual Studio 2015 y versiones posteriores, el [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) clases y tipos relacionados en ppltasks.h usan ThreadPool de Windows como programador. Este tema ya no se aplica a los tipos que se definen en ppltasks.h. Los algoritmos paralelos, como parallel_for, siguen usando Runtime de simultaneidad como programador predeterminado.

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

El Programador de tareas programa y coordina las tareas en tiempo de ejecución. Un *tarea* es una unidad de trabajo que realiza un trabajo específico. Normalmente, es posible ejecutar en paralelo varias tareas. Son ejemplos de tareas los trabajos que realizan los elementos de grupo de tareas, los algoritmos paralelos y los agentes asincrónicos.

El Programador de tareas administra los detalles relacionados con la programación eficaz de las tareas en equipos con varios recursos informáticos. Asimismo, usa las características más recientes del sistema operativo subyacente. Por lo tanto, las aplicaciones que usan Runtime de simultaneidad escalan y mejoran automáticamente el hardware con capacidades expandidas.

[En comparación con otros modelos de simultaneidad](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) se describen las diferencias entre los mecanismos de programación preferentes y cooperativas. El Programador de tareas usa la programación cooperativa y un algoritmo de robo de trabajo con el programador preferente del sistema operativo. De este modo, consigue realizar el mayor uso posible de los recursos de procesamiento.

El Runtime de simultaneidad proporciona un programador predeterminado, de modo que no es necesario administrar los detalles de infraestructura. Por lo tanto, en la mayoría de los casos, no usará el Programador de tareas directamente. Sin embargo, para satisfacer las necesidades de calidad de la aplicación, puede usar este programador para proporcionar su propia directiva de programación, o asociar programadores a tareas específicas. Por ejemplo, supongamos que dispone de una rutina de ordenación en paralelo que, como máximo, puede escalarse a través de cuatro procesadores. Puede usar *directivas del programador* para crear un programador que genera no más de cuatro tareas simultáneas. Si ejecuta la rutina de ordenación en este programador, habilitará al resto de programadores activos para usar los recursos de procesamiento restantes.

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Instancias de Scheduler](../../parallel/concrt/scheduler-instances.md)|Describe las instancias del programador y cómo usar las clases `concurrency::Scheduler` y `concurrency::CurrentScheduler` para administrarlas. Use las instancias del programador para asociar directivas de programación explícitas con tipos concretos de cargas de trabajo.|
|[Directivas de Scheduler](../../parallel/concrt/scheduler-policies.md)|Describe el rol de las directivas del programador. Use las instancias del programador para controlar la estrategia de administración de tareas del programador.|
|[Grupos de programación](../../parallel/concrt/schedule-groups.md)|Describe el rol de los grupos de programación. Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas (por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador).|
|[Tareas ligeras](../../parallel/concrt/lightweight-tasks.md)|Describe el rol de las tareas ligeras. Las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad.|
|[Contextos](../../parallel/concrt/contexts.md)|Describe el rol de los contextos, la función `concurrency::wait` y la clase `concurrency::Context`. Use esta funcionalidad si necesita controlar cuándo los contextos deben realizar acciones de bloqueo, desbloqueo y rentabilidad, o cuándo debe habilitarse la suscripción excesiva en la aplicación.|
|[Funciones de administración de memoria](../../parallel/concrt/memory-management-functions.md)|Describe las funciones `concurrency::Alloc` y `concurrency::Free`. Para mejorar el rendimiento de la memoria, estas funciones pueden asignar y liberar memoria de forma simultánea.|
|[En comparación con otros modelos de simultaneidad](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Describe las diferencias existentes entre los mecanismos de programación cooperativa y preferente.|
|[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe cómo usar diferentes modelos de procesamiento paralelo, como los algoritmos paralelos, en las aplicaciones.|
|[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)|Describe cómo se deben usar los agentes asincrónicos en las aplicaciones.|
|[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)|Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a los temas relacionados.|
