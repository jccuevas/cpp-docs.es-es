---
title: StopAndRelogTracingSession
description: La C++ referencia de la función STOPANDRELOGTRACINGSESSION del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334203"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `StopAndRelogTracingSession` detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. Una sesión de registro se inicia inmediatamente mediante el archivo temporal como una entrada. El último seguimiento reiniciado por la sesión de registro se guarda en un archivo especificado por el autor de la llamada. Los ejecutables que llaman a esta función deben tener privilegios de administrador.

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

*nombresesión*\
Nombre de la sesión de seguimiento que se va a detener. Use el mismo nombre de sesión que el que se pasó a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

\ *outputLogFile*
Archivo en el que se va a escribir el seguimiento reiniciado por la sesión de registro.

*estadísticas*\
Puntero a un objeto de [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndRelogTracingSession` escribe estadísticas de la colección de seguimiento en este objeto antes de devolver.

\ *numberOfAnalysisPasses*
El número de pasos de análisis que se van a ejecutar en el seguimiento. El seguimiento se pasa a través del grupo de analizador proporcionado una vez por cada paso del análisis.

\ *systemEventsRetentionFlags*
Una máscara de [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) que especifica qué eventos ETW del sistema mantener en el seguimiento que se ha reiniciado.

\ *analyzerGroup*
El grupo de analizador que se usa para la fase de análisis de la sesión de reregistro. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de Analyzer. Si desea usar un grupo de analizador dinámico Obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero debe encapsularlo dentro de un grupo de analizador estático pasando su dirección a `MakeStaticAnalyzerGroup`.

\ *reloggerGroup*
El grupo de reregistradores que vuelve a registrar los eventos en el archivo de seguimiento especificado en *outputLogFile*. Llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) para crear un grupo de registro. Si desea usar un grupo de registradores dinámicos Obtenido de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), primero debe encapsularlo dentro de un grupo de registradores estáticos pasando su dirección a `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

### <a name="remarks"></a>Comentarios

El seguimiento de entrada se pasa a través del grupo de analizador *numberOfAnalysisPasses* veces. No hay ninguna opción similar para las fases de registro. El seguimiento se pasa con el grupo de reregistradores solo una vez, una vez completados todos los pasos del análisis.

No se admite el reregistro de eventos del sistema como ejemplos de CPU desde una clase de reregistrador. Use el parámetro *systemEventsRetentionFlags* para decidir qué eventos del sistema deben conservarse en el seguimiento de salida.

::: moniker-end
