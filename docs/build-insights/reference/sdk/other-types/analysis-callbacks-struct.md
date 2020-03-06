---
title: Estructura de ANALYSIS_CALLBACKS
description: El C++ SDK de Build insights ANALYSIS_CALLBACKS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334149"
---
# <a name="analysis_callbacks-structure"></a>Estructura de ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura de `ANALYSIS_CALLBACKS` se utiliza al inicializar un objeto [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Especifica las funciones a las que se llama durante el análisis o el registro de un seguimiento de seguimiento de eventos para Windows (ETW).

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
| `OnSimpleEvent` | Se llama para procesar un evento simple. |
| `OnTraceInfo` | En el caso de las sesiones de análisis, se llama al principio de cada paso del análisis. En el caso de las sesiones de registro, se llama al principio de cada fase de análisis y de nuevo al principio del paso de registro. Solo se llama a esta función después de que se haya llamado a OnBeginAnalysisPass. |
| `OnBeginAnalysis` | En el caso de las sesiones de análisis, se llama a antes de que haya comenzado cualquier paso del análisis. En el caso de las sesiones de registro, se llama dos veces antes de que se inicie la fase de análisis: una vez para anunciar el inicio de la sesión de registro y otra vez para anunciar el comienzo de la fase de análisis. |
| `OnEndAnalysis` | En las sesiones de análisis, se llama a esta función una vez finalizados todos los pasos del análisis. En el caso de las sesiones de registro, se llama a esta función cuando han finalizado todos los pasos de análisis de la fase de análisis. A continuación, se llama de nuevo una vez finalizada la fase de reregistro. |
| `OnBeginAnalysisPass` | Se llama cuando se inicia un paso de análisis o el paso de registro, antes de procesar cualquier evento. |
| `OnEndAnalysisPass` | Se llama al finalizar un paso de análisis o el paso de registro, después de procesar todos los eventos. |

## <a name="remarks"></a>Comentarios

La fase de análisis de una sesión de registro se considera parte de la sesión de reregistro y puede contener varios pasos de análisis. Por esta razón, se llama a `OnBeginAnalysis` dos veces en una fila al principio de una sesión de reinicio. al final de la fase de análisis, se llama a `OnEndAnalysis` antes de iniciar la fase de reregistro y, una vez más, al final de la fase de reregistro. La fase de reregistro siempre contiene un único paso de registro.

Es posible que los analizadores formen parte del análisis y de la fase de reregistro de una sesión de reinicio. Estos analizadores pueden determinar qué fase está actualmente en curso realizando un seguimiento de los pares de llamadas OnBeginAnalysis y `OnEndAnalysis`. Dos llamadas `OnBeginAnalysis` sin ninguna llamada `OnEndAnalysis` significa que la fase de análisis está en curso. Dos llamadas `OnBeginAnalysis` y una llamada `OnEndAnalysis` significa que la fase de reregistro está en curso. Dos llamadas a OnBeginAnalysis y dos `OnEndAnalysis` significan que ambas fases han finalizado.

Todos los miembros de la estructura `ANALYSIS_CALLBACKS` deben apuntar a una función válida. Para obtener más información sobre las firmas de funciones aceptadas, vea [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)y [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
