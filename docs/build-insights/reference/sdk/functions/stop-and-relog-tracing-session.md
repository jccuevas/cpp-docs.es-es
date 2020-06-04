---
title: StopAndRelogTracingSession
description: La referencia de la función StopAndRelogTracingSession del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323667"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopAndRelogTracingSession` función detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. A continuación, se inicia inmediatamente una sesión de resregistración utilizando el archivo temporal como entrada. El seguimiento final reregistrado generado por la sesión de reregistro se guarda en un archivo especificado por el autor de la llamada. Los ejecutables que llamen a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parámetros

*sessionName*\
El nombre de la sesión de seguimiento que se debe detener. Utilice el mismo nombre de sesión que el pasado a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
El archivo en el que se escribe el seguimiento reescrito generado por la sesión de reregistro.

*Estadísticas*\
Puntero a un objeto [TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndRelogTracingSession`escribe estadísticas de recopilación de seguimiento en este objeto antes de devolver.

*numberOfAnalysisPasses*\
El número de pasos de análisis pasa para ejecutarse en el seguimiento. El seguimiento pasa a través del grupo de analizador proporcionado una vez por paso de análisis.

*systemEventsRetentionFlags*\
Una máscara de bits [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) que especifica qué eventos ETW del sistema se deben mantener en el seguimiento reiniciado.

*analyzerGroup*\
El grupo de analizadores utilizado para la fase de análisis de la sesión de recorrección. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de analizadores. Si desea utilizar un grupo de analizadores dinámicos obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero `MakeStaticAnalyzerGroup`entibrelo dentro de un grupo de analizadores estáticos pasando su dirección a .

*reloggerGroup*\
El grupo de reregistrador que vuelve a registrar eventos en el archivo de seguimiento especificado en *outputLogFile*. Llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) para crear un grupo de reregistradores. Si desea utilizar un grupo de reregistrador dinámico obtenido de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), primero entibrecómose dentro de un grupo de reregistrador estático pasando su dirección a `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

### <a name="remarks"></a>Observaciones

El seguimiento de entrada se pasa a través del grupo de *analizadornumberOfAnalysisPasses* times. No hay una opción similar para volver a registrar pases. La traza se pasa a través del grupo del registrador una sola vez, después de que se completen todas las pasadas de análisis.

No se admite el reregistro de eventos del sistema como muestras de CPU desde una clase de relogger. Utilice el parámetro *systemEventsRetentionFlags* para decidir qué eventos del sistema se mantendrán en el seguimiento de salida.

::: moniker-end
