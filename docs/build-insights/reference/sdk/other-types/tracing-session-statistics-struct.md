---
title: Estructura de TRACING_SESSION_STATISTICS
description: El C++ SDK de Build insights TRACING_SESSION_OPTIONS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333867"
---
# <a name="tracing_session_statistics-structure"></a>Estructura de TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `TRACING_SESSION_STATISTICS` describe las estadísticas de un seguimiento que se recopiló. Los campos se establecen al detener una sesión de seguimiento.

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
| `MSVCEventsLost` | Número de eventos MSVC que se quitaron. |
| `MSVCBuffersLost` | El número de búferes de eventos MSVC que se quitaron. |
| `SystemEventsLost` | Número de eventos del sistema que se quitaron. |
| `SystemBuffersLost` | El número de búferes de eventos del sistema que se quitaron. |

## <a name="remarks"></a>Comentarios

Esta estructura se rellena cuando se llama a las siguientes funciones:

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
