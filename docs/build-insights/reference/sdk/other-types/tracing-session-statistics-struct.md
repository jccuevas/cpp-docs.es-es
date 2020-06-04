---
title: estructura TRACING_SESSION_STATISTICS
description: El SDK de C++ Build Insights TRACING_SESSION_OPTIONS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323377"
---
# <a name="tracing_session_statistics-structure"></a>estructura TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRACING_SESSION_STATISTICS` estructura describe las estadísticas de un seguimiento que se recopiló. Sus campos se establecen al detener una sesión de seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `MSVCEventsLost` | El número de eventos MSVC que se descartaron. |
| `MSVCBuffersLost` | El número de búferes de eventos MSVC que se quitaron. |
| `SystemEventsLost` | El número de eventos del sistema que se han eliminado. |
| `SystemBuffersLost` | El número de búferes de eventos del sistema que se quitaron. |

## <a name="remarks"></a>Observaciones

Esta estructura se rellena al llamar a las siguientes funciones:

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessiona](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionw](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
