---
title: estructura ANALYSIS_CALLBACKS
description: El SDK de C++ Build Insights ANALYSIS_CALLBACKS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323509"
---
# <a name="analysis_callbacks-structure"></a>estructura ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ANALYSIS_CALLBACKS` estructura se utiliza al inicializar un objeto [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Especifica qué funciones llamar durante el análisis o el reregistro de un seguimiento de seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `OnStartActivity` | Se llama para procesar un evento de inicio de actividad. |
| `OnStopActivity` | Se llama para procesar un evento de detención de actividad. |
| `OnSimpleEvent` | Llamado para procesar un evento simple. |
| `OnTraceInfo` | Para sesiones de análisis, llamadas al principio de cada paso de análisis. Para las sesiones de reregistro, se llama al principio de cada paso de análisis y de nuevo al principio del pase de relogging. Esta función sólo se llama después de OnBeginAnalysisPass se ha llamado. |
| `OnBeginAnalysis` | Para sesiones de análisis, llamadas antes de que se haya iniciado cualquier paso de análisis. Para las sesiones de relogging, llamadas dos veces antes de que se haya iniciado la fase de análisis: una vez para anunciar el inicio de la sesión de relogging, y una vez más para anunciar el comienzo de la fase de análisis. |
| `OnEndAnalysis` | Para las sesiones de análisis, se llama a esta función una vez finalizados todos los pases de análisis. Para las sesiones de reregistro, se llama a esta función cuando todos los pases de análisis de la fase de análisis han finalizado. Luego, se llama de nuevo después de que el pase de relogging haya terminado. |
| `OnBeginAnalysisPass` | Se llama al iniciar un pase de análisis o el paso de relogging, antes de procesar cualquier evento. |
| `OnEndAnalysisPass` | Se llama al finalizar un paso de análisis o el paso de relogging, después de procesar todos los eventos. |

## <a name="remarks"></a>Observaciones

La fase de análisis de una sesión de reregistro se considera parte de la sesión de recorrección y puede contener varias pasadas de análisis. Por este `OnBeginAnalysis` motivo, se llama dos veces seguidas al principio de una sesión de reslogging. `OnEndAnalysis`se llama al final de la fase de análisis, antes de iniciar la fase de reregistro, y una vez más al final de la fase de reregistro. La fase de reregistro siempre contiene una sola pasada de recorrección.

Es posible que los analizadores formen parte tanto del análisis como de la fase de reregistro de una sesión de relogging. Estos analizadores pueden determinar qué fase está actualmente en `OnEndAnalysis` curso mediante el seguimiento de los pares OnBeginAnalysis y call. Dos `OnBeginAnalysis` llamadas `OnEndAnalysis` sin ninguna llamada significa que la fase de análisis está en curso. Dos `OnBeginAnalysis` llamadas `OnEndAnalysis` y una llamada significa que la fase de relogging está en curso. Dos OnBeginAnalysis `OnEndAnalysis` y dos llamadas significa que ambas fases han finalizado.

Todos los `ANALYSIS_CALLBACKS` miembros de la estructura deben apuntar a una función válida. Para obtener más información sobre las firmas de función aceptadas, vea [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)y [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
