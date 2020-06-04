---
title: Herramientas de diagnóstico paralelo (Runtime de simultaneidad)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 34b2421dfc53deeb35dcc659a8d555983e583737
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510505"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Herramientas de diagnóstico paralelo (Runtime de simultaneidad)

Visual Studio proporciona amplia compatibilidad para depurar aplicaciones de varios subprocesos y generar perfiles de estas.

## <a name="debugging"></a>Depuración

El depurador de Visual Studio incluye la ventana **pilas paralelas** , la ventana **tareas paralelas** y la ventana **inspección paralela** . Para obtener más información, vea [Tutorial: Depurar una aplicación](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) paralela [y cómo: Use la ventana](/visualstudio/debugger/how-to-use-the-parallel-watch-window)inspección paralela.

## <a name="profiling"></a>Generación de perfiles

Las herramientas de generación de perfiles proporcionan tres vistas de datos que muestran información gráfica, tabular y numérica sobre cómo una aplicación multiproceso interactúa con sí misma y con otros programas. Las vistas permiten identificar rápidamente áreas de preocupación y navegar desde puntos de las pantallas gráficas hasta pilas de llamadas, sitios de llamada y código fuente. Para más información, consulte [Visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Seguimiento de eventos

El Runtime de simultaneidad usa el [seguimiento de eventos para Windows](/windows/win32/ETW/event-tracing-portal) (ETW) para notificar a las herramientas de instrumentación, como los generadores, cuando se producen varios eventos. Estos eventos incluyen Cuándo se activa o desactiva un programador, cuando un contexto comienza, finaliza, bloquea, desbloquea o produce, y cuando se inicia o finaliza un algoritmo paralelo.

Las herramientas como el [visualizador de simultaneidad](/visualstudio/profiling/concurrency-visualizer) usan esta funcionalidad; por lo tanto, normalmente no es necesario trabajar directamente con estos eventos. Sin embargo, estos eventos son útiles cuando se desarrolla un generador de perfiles personalizado o cuando se usan herramientas de seguimiento de eventos como [Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628).

El Runtime de simultaneidad genera estos eventos solo cuando está habilitado el seguimiento. Llame a la función [Concurrency:: enabletracing (](reference/concurrency-namespace-functions.md#enabletracing) para habilitar el seguimiento de eventos y la función Concurrency [::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing) para deshabilitar el seguimiento.

En la tabla siguiente se describen los eventos que genera el tiempo de ejecución cuando se habilita el seguimiento de eventos:

|Evento|DESCRIPCIÓN|Valor|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|Identificador del proveedor de ETW para el Runtime de simultaneidad.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|Marca los eventos que están relacionados con los contextos.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|Marca la entrada y la salida a las llamadas al algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Marca la entrada y la salida a las llamadas al algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) .|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Marca la entrada y la salida a las llamadas al algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) .|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|Marca los eventos relacionados con el [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|Marca los eventos relacionados con los procesadores virtuales.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

El Runtime de simultaneidad define, pero actualmente no genera los siguientes eventos. El tiempo de ejecución reserva estos eventos para un uso futuro:

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

La enumeración [Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) especifica las posibles operaciones a las que un evento realiza un seguimiento. Por ejemplo, en la entrada del `parallel_for` algoritmo, el tiempo de ejecución genera el `PPLParallelForEventGuid` evento y `CONCRT_EVENT_START` proporciona como la operación. Antes de `parallel_for` que el algoritmo devuelva, el tiempo `PPLParallelForEventGuid` de ejecución genera `CONCRT_EVENT_END` de nuevo el evento y proporciona como la operación.

En el ejemplo siguiente se muestra cómo habilitar el seguimiento para una llamada `parallel_for`a. El tiempo de ejecución no realiza un seguimiento de `parallel_for` la primera llamada a porque el seguimiento no está habilitado. La llamada a `EnableTracing` permite al motor en tiempo de ejecución realizar un `parallel_for`seguimiento de la segunda llamada a.

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

El tiempo de ejecución realiza un seguimiento del número de `EnableTracing` veces `DisableTracing`que se llama a y. Por lo tanto, si `EnableTracing` llama a varias veces, debe `DisableTracing` llamar al mismo número de veces para deshabilitar el seguimiento.

## <a name="see-also"></a>Vea también

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)
