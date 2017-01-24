---
title: "Programador de tareas (Runtime de simultaneidad) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "tareas ligeras [Runtime de simultaneidad]"
  - "suscripción excesiva [Runtime de simultaneidad]"
  - "grupos de programación [Runtime de simultaneidad]"
  - "instancias del programador [Runtime de simultaneidad]"
  - "directivas del programador [Runtime de simultaneidad]"
  - "programador de tareas [Runtime de simultaneidad]"
  - "programador de tareas [Runtime de simultaneidad], tareas ligeras"
  - "programador de tareas [Runtime de simultaneidad], suscripción excesiva"
  - "programador de tareas [Runtime de simultaneidad], grupos de programación"
  - "programador de tareas [Runtime de simultaneidad], instancias del programador"
  - "programador de tareas [Runtime de simultaneidad], directivas del programador"
  - "programador de tareas [Runtime de simultaneidad], wait (función)"
  - "wait (función) [Runtime de simultaneidad]"
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
caps.latest.revision: 42
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Programador de tareas (Runtime de simultaneidad)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los temas de esta parte de la documentación describen las características relevantes del Programador de tareas de Runtime de simultaneidad.  El Programador de tareas resulta útil para ajustar el rendimiento del código existente que usa Runtime de simultaneidad.  
  
> [!IMPORTANT]
>  El Programador de tareas no está disponible en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información, consulte [Crear operaciones asincrónicas en C\+\+ para aplicaciones de la Tienda Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
>   
>  En Visual Studio de 2015 y versiones posteriores, la clase [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) y los tipos relacionados de ppltasks.h usan ThreadPool de Windows como programador.  Este tema ya no se aplica a los tipos que se definen en ppltasks.h.  Los algoritmos paralelos, como parallel\_for, siguen usando Runtime de simultaneidad como programador predeterminado.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación.  El programador de tareas permite ajustar el rendimiento de las aplicaciones por lo que, si no está familiarizado con Runtime de simultaneidad, se recomienda comenzar con las bibliotecas de [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).  
  
 El Programador de tareas programa y coordina las tareas en tiempo de ejecución.  Una *tarea* es una unidad de trabajo que realiza un trabajo específico.  Normalmente, es posible ejecutar en paralelo varias tareas.  Son ejemplos de tareas los trabajos que realizan los elementos de grupo de tareas, los algoritmos paralelos y los agentes asincrónicos.  
  
 El Programador de tareas administra los detalles relacionados con la programación eficaz de las tareas en equipos con varios recursos informáticos.  Asimismo, usa las características más recientes del sistema operativo subyacente.  Por lo tanto, las aplicaciones que usan Runtime de simultaneidad escalan y mejoran automáticamente el hardware con capacidades expandidas.  
  
 En este artículo, que [Comparar con otros modelos de simultaneidad](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md), se describen las diferencias existentes entre los mecanismos de programación cooperativa y preferente.  El Programador de tareas usa la programación cooperativa y un algoritmo de robo de trabajo con el programador preferente del sistema operativo. De este modo, consigue realizar el mayor uso posible de los recursos de procesamiento.  
  
 Runtime de simultaneidad proporciona un programador predeterminado, de modo que no es necesario administrar los detalles de infraestructura.  Por lo tanto, en la mayoría de los casos, no usará el Programador de tareas directamente.  Sin embargo, para satisfacer las necesidades de calidad de la aplicación, puede usar este programador para proporcionar su propia directiva de programación, o asociar programadores a tareas específicas.  Por ejemplo, supongamos que dispone de una rutina de ordenación en paralelo que, como máximo, puede escalarse a través de cuatro procesadores.  Con las *directivas del programador* puede crear un programador que, como máximo, genere cuatro tareas simultáneas.  Si ejecuta la rutina de ordenación en este programador, habilitará al resto de programadores activos para usar los recursos de procesamiento restantes.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Instancias del programador](../../parallel/concrt/scheduler-instances.md)|Describe las instancias del programador y cómo usar las clases `concurrency::Scheduler` y `concurrency::CurrentScheduler` para administrarlas.  Use las instancias del programador para asociar directivas de programación explícitas con tipos concretos de cargas de trabajo.|  
|[Directivas del programador](../../parallel/concrt/scheduler-policies.md)|Describe el rol de las directivas del programador.  Use las instancias del programador para controlar la estrategia de administración de tareas del programador.|  
|[Grupos de programación](../../parallel/concrt/schedule-groups.md)|Describe el rol de los grupos de programación.  Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas \(por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador\).|  
|[Tareas ligeras](../../parallel/concrt/lightweight-tasks.md)|Describe el rol de las tareas ligeras.  Las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad.|  
|[Contextos](../../parallel/concrt/contexts.md)|Describe el rol de los contextos, la función `concurrency::wait` y la clase `concurrency::Context`.  Use esta funcionalidad si necesita controlar cuándo los contextos deben realizar acciones de bloqueo, desbloqueo y rentabilidad, o cuándo debe habilitarse la suscripción excesiva en la aplicación.|  
|[Funciones de administración de memoria](../../parallel/concrt/memory-management-functions.md)|Describe las funciones `concurrency::Alloc` y `concurrency::Free`.  Para mejorar el rendimiento de la memoria, estas funciones pueden asignar y liberar memoria de forma simultánea.|  
|[Comparar con otros modelos de simultaneidad](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Describe las diferencias existentes entre los mecanismos de programación cooperativa y preferente.|  
|[Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe cómo se deben usar varios modelos paralelos \(como los algoritmos paralelos\) en las aplicaciones.|  
|[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)|Describe cómo se deben usar los agentes asincrónicos en las aplicaciones.|  
|[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)|Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a los temas relacionados.|