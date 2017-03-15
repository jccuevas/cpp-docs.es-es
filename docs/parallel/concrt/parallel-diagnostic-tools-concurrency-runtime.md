---
title: "Herramientas de diagn&#243;stico paralelo (Runtime de simultaneidad) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Herramientas de diagnóstico paralelo [Runtime de simultaneidad]"
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Herramientas de diagn&#243;stico paralelo (Runtime de simultaneidad)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] proporciona amplia compatibilidad con la depuración y la generación de perfiles de las aplicaciones multiproceso.  
  
## Depuración  
 El depurador de Visual Studio incluye la ventana de **Pilas paralelas** , la ventana de **Tareas paralelas** , y la ventana de **Inspección paralela** .  Para obtener más información, vea [Tutorial: Depurar una aplicación paralela](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md) y [Cómo: Utilizar la Ventana Inspección paralela](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md).  
  
## Generación de perfiles  
 Las herramientas de generación de perfiles proporcionan tres vistas de datos que muestran información numérica, gráfica y tabular sobre cómo una aplicación multithreading interactúa con sí misma y con otros programas.  Las vistas le permiten identificar áreas problemáticas rápidamente y navegar de los puntos en las presentaciones gráficas a las pilas de llamadas, sitios de llamada y código fuente.  Para obtener más información, vea [Visualizador de simultaneidad](../Topic/Concurrency%20Visualizer.md).  
  
## Seguimiento de eventos  
 El runtime de simultaneidad usa el [seguimiento de eventos para Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) \(ETW\) para notificar a las herramientas de instrumentación, por ejemplo, a los generadores de perfiles, cuándo tienen lugar los distintos eventos.  Estos eventos incluyen cuando se activa o desactiva un programador, cuando se inicia, finaliza, se bloquea, se desbloquea o produce resultados un contexto y cuando se inicia o finaliza un algoritmo paralelo.  
  
 Las herramientas como [Visualizador de simultaneidad](../Topic/Concurrency%20Visualizer.md) utilizan esta funcionalidad; por consiguiente, no suele ser necesario trabajar con estos eventos directamente.  Sin embargo, estos eventos son útiles cuando se está desarrollando un generador personalizado o cuando se usan las herramientas de seguimiento de eventos como. [Xperf](http://go.microsoft.com/fwlink/?LinkID=160628)  
  
 El runtime de simultaneidad genera estos eventos solo cuando está habilitado el seguimiento.  Llame a la función de [el concurrency::EnableTracing](../Topic/EnableTracing%20Function.md) para habilitar la traza de eventos y la función de [el concurrency::DisableTracing](../Topic/DisableTracing%20Function.md) para deshabilitar el seguimiento.  
  
 En la tabla siguiente se describen los eventos que genera el runtime cuando se habilita el seguimiento de eventos:  
  
|Evento|Descripción|Valor|  
|------------|-----------------|-----------|  
|[concurrency::ConcRT\_ProviderGuid](../Topic/ConcRT_ProviderGuid%20Constant.md)|Identificador del proveedor ETW del runtime de simultaneidad.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[concurrency::ContextEventGuid](../Topic/ContextEventGuid%20Constant.md)|Marca los eventos relacionados con los contextos.|`5727a00f-50be-4519-8256-f7699871fecb`|  
|[concurrency::PPLParallelForEventGuid](../Topic/PPLParallelForEventGuid%20Constant.md)|Marca la entrada y la salida de las llamadas al algoritmo de [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) .|`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[concurrency::PPLParallelForeachEventGuid](../Topic/PPLParallelForeachEventGuid%20Constant.md)|Marca la entrada y la salida de las llamadas al algoritmo de [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) .|`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[concurrency::PPLParallelInvokeEventGuid](../Topic/PPLParallelInvokeEventGuid%20Constant.md)|Marca la entrada y la salida de las llamadas al algoritmo de [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) .|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[concurrency::SchedulerEventGuid](../Topic/SchedulerEventGuid%20Constant.md)|Marca los eventos relacionados con el [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[concurrency::VirtualProcessorEventGuid](../Topic/VirtualProcessorEventGuid%20Constant.md)|Marca los eventos relacionados con los procesadores virtuales.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 El runtime de simultaneidad define, pero no genera realmente, los siguientes eventos.  El runtime reserva estos eventos para uso futuro:  
  
-   [concurrency::ConcRTEventGuid](../Topic/ConcRTEventGuid%20Constant.md)  
  
-   [concurrency::ScheduleGroupEventGuid](../Topic/SchedulerEventGuid%20Constant.md)  
  
-   [concurrency::ChoreEventGuid](../Topic/ChoreEventGuid%20Constant.md)  
  
-   [concurrency::LockEventGuid](../Topic/LockEventGuid%20Constant.md)  
  
-   [concurrency::ResourceManagerEventGuid](../Topic/ResourceManagerEventGuid%20Constant.md)  
  
 La enumeración de [concurrency::ConcRT\_EventType](../Topic/ConcRT_EventType%20Enumeration.md) especifica las posibles operaciones que un evento sigue.  Por ejemplo, en la entrada del algoritmo `parallel_for`, el runtime genera el evento `PPLParallelForEventGuid` y proporciona `CONCRT_EVENT_START` como la operación.  Antes de que el algoritmo `parallel_for` devuelva un resultado, el runtime genera el evento `PPLParallelForEventGuid` y proporciona `CONCRT_EVENT_END` como la operación.  
  
 En el ejemplo siguiente se muestra cómo habilitar el seguimiento para una llamada a `parallel_for`.  El runtime no realiza el seguimiento de la primera llamada a `parallel_for` porque el seguimiento no está habilitado.  La llamada a `EnableTracing` permite al runtime hacer un seguimiento de la segunda llamada a `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/CPP/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 El runtime realiza el seguimiento del número de veces que se llama a `EnableTracing` y `DisableTracing`.  Por consiguiente, si se llama a `EnableTracing` varias veces, se debe llamar a `DisableTracing` el mismo número de veces para deshabilitar el seguimiento.  
  
## Vea también  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)