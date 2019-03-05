---
title: Herramientas de diagnóstico paralelo (Runtime de simultaneidad)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 2af1898312a4f448d618fcfc4e43ea93f5f0bc76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302785"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Herramientas de diagnóstico paralelo (Runtime de simultaneidad)

Visual Studio proporciona amplia compatibilidad para depurar aplicaciones de varios subprocesos y generar perfiles de estas.

## <a name="debugging"></a>Depuración

El depurador de Visual Studio incluye la **pilas paralelas** ventana, **tareas paralelas** ventana, y **inspección paralela** ventana. Para obtener más información, vea [Tutorial: Depurar una aplicación paralela](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) y [Cómo: Utilice la ventana Inspección paralela](/visualstudio/debugger/how-to-use-the-parallel-watch-window).

## <a name="profiling"></a>Generación de perfiles

Las herramientas de generación de perfiles proporcionan tres vistas de datos que muestran información gráfica, tabular y numérica acerca de cómo se interactúa una aplicación multiproceso consigo misma y con otros programas. Las vistas le permiten identificar rápidamente las áreas de preocupación y para navegar desde los puntos en las pantallas gráficas a pilas de llamadas, sitios de llamada y código fuente. Para más información, consulte [Visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Seguimiento de eventos

El Runtime de simultaneidad usa [seguimiento de eventos para Windows](/windows/desktop/ETW/event-tracing-portal) (ETW) para notificar a las herramientas de instrumentación, como los generadores de perfiles, cuando se producen varios eventos. Estos eventos incluyen cuando se activa o desactiva un programador, cuando un contexto comienza, finaliza, bloquea, desbloquea o da como resultado, y cuando un algoritmo paralelo comienza o finaliza.

Herramientas como el [visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer) utilizar esta funcionalidad; por lo tanto, normalmente no tendrá que trabajar directamente con estos eventos. Sin embargo, estos eventos son útiles cuando se está desarrollando un generador de perfiles personalizado o al usar herramientas de seguimiento de eventos como [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).

El Runtime de simultaneidad genera estos eventos solo cuando está habilitada la traza. Llame a la [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) función para habilitar el seguimiento de eventos y el [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) función para deshabilitar el seguimiento.

En la tabla siguiente se describe los eventos que el tiempo de ejecución genera cuando se habilita el seguimiento de eventos:

|evento|Descripción|Valor|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|El identificador de proveedor ETW para el Runtime de simultaneidad.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|Marca los eventos relacionados con contextos.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|Marca la entrada y salida para las llamadas a la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo.|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Marca la entrada y salida para las llamadas a la [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo.|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Marca la entrada y salida para las llamadas a la [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo.|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|Marca los eventos relacionados con el [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|Marca los eventos relacionados con procesadores virtuales.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

El Runtime de simultaneidad se define, pero no actualmente elevar, los siguientes eventos. El tiempo de ejecución reserva estos eventos para un uso futuro:

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

El [concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) enumeración especifica las posibles operaciones que realiza el seguimiento de un evento. Por ejemplo, en la entrada de la `parallel_for` algoritmo, el tiempo de ejecución genera el `PPLParallelForEventGuid` eventos y proporciona `CONCRT_EVENT_START` como la operación. Antes de la `parallel_for` devuelve el algoritmo, el tiempo de ejecución genera otra vez el `PPLParallelForEventGuid` eventos y proporciona `CONCRT_EVENT_END` como la operación.

El ejemplo siguiente muestra cómo habilitar el seguimiento de una llamada a `parallel_for`. El tiempo de ejecución no realizar el seguimiento de la primera llamada a `parallel_for` porque el seguimiento no está habilitado. La llamada a `EnableTracing` permite que el tiempo de ejecución para realizar un seguimiento de la segunda llamada a `parallel_for`.

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

El tiempo de ejecución realiza un seguimiento del número de veces que se llama a `EnableTracing` y `DisableTracing`. Por lo tanto, si se llama a `EnableTracing` varias veces, debe llamar a `DisableTracing` el mismo número de veces con el fin de deshabilitar el seguimiento.

## <a name="see-also"></a>Vea también

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)
