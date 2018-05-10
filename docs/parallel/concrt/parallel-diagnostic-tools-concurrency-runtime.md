---
title: Herramientas de diagnóstico (Runtime de simultaneidad) en paralelo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cd3ce4c86332719e299c11fee3ffbee8b41c14f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Herramientas de diagnóstico paralelo (Runtime de simultaneidad)
[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] proporciona amplia compatibilidad para depurar aplicaciones de varios subprocesos y generar perfiles de estas.  
  
## <a name="debugging"></a>Depuración  
 El depurador de Visual Studio incluye la **pilas paralelas** ventana, **tareas paralelas** ventana, y **inspección paralela** ventana. Para obtener más información, consulte [Tutorial: depurar una aplicación paralela](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) y [Cómo: utilizar la ventana Inspección paralela](/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
## <a name="profiling"></a>Generación de perfiles  
 Las herramientas de generación de perfiles proporcionan tres vistas de datos que mostrar gráfica, tabular y numérica información sobre cómo una aplicación multiproceso consigo misma y con otros programas. Las vistas le permiten identificar rápidamente las áreas problemáticas y para navegar de puntos en las pantallas gráficas a pilas de llamadas, sitios de llamada y código fuente. Para más información, consulte [Visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="event-tracing"></a>Seguimiento de eventos  
 El Runtime de simultaneidad usa [seguimiento de eventos para Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) (ETW) para notificar a las herramientas de instrumentación, como los generadores de perfiles, cuando se producen varios eventos. Estos eventos incluyen cuando se activa o desactiva un programador, cuando un contexto comienza, finaliza, se bloquea, desbloquea o da como resultado, y cuando un algoritmo paralelo empieza o termina.  
  
 Herramientas como el [visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer) utilizar esta funcionalidad; por lo tanto, normalmente no tendrá que trabajar directamente con estos eventos. Sin embargo, estos eventos son útiles cuando se está desarrollando un generador de perfiles personalizado o cuando se usan herramientas de traza de eventos como [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).  
  
 El Runtime de simultaneidad genera estos eventos solo cuando se habilita el seguimiento. Llame a la [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) función para habilitar el seguimiento de eventos y el [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) función para deshabilitar el seguimiento.  
  
 En la tabla siguiente se describe los eventos que el tiempo de ejecución que se genera cuando se habilita el seguimiento de eventos:  
  
|evento|Descripción|Valor|  
|-----------|-----------------|-----------|  

|[Concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| El identificador del proveedor de ETW para el Runtime de simultaneidad. |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[Concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Marca los eventos que están relacionados con contextos. |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[Concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Marca la entrada y salida en llamadas a la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo. |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[Concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Marca la entrada y salida en llamadas a la [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo. |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[Concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Marca la entrada y salida en llamadas a la [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo. |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[Concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Marca los eventos que están relacionados con el [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md). |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[Concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Marca los eventos que están relacionados con los procesadores virtuales. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 El Runtime de simultaneidad se define, pero no actualmente generar, los siguientes eventos. El tiempo de ejecución reserva estos eventos para un uso futuro:  
  
-   [Concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [Concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [Concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [Concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [Concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 El [concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) enumeración especifica las posibles operaciones que realiza el seguimiento de un evento. Por ejemplo, en la entrada de la `parallel_for` algoritmo, el tiempo de ejecución genera el `PPLParallelForEventGuid` eventos y proporciona `CONCRT_EVENT_START` como la operación. Antes de la `parallel_for` devuelve el algoritmo, el tiempo de ejecución genera de nuevo el `PPLParallelForEventGuid` eventos y proporciona `CONCRT_EVENT_END` como la operación.  
  
 En el ejemplo siguiente se muestra cómo habilitar el seguimiento de una llamada a `parallel_for`. El tiempo de ejecución no realizar el seguimiento de la primera llamada a `parallel_for` porque el seguimiento no está habilitado. La llamada a `EnableTracing` permite que el tiempo de ejecución realizar el seguimiento de la segunda llamada a `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 El tiempo de ejecución realiza un seguimiento del número de veces que se llama a `EnableTracing` y `DisableTracing`. Por lo tanto, si se llama a `EnableTracing` varias veces, debe llamar a `DisableTracing` el mismo número de veces con el fin de deshabilitar el seguimiento.  
  
## <a name="see-also"></a>Vea también  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)

