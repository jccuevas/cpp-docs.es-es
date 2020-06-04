---
title: StopAndAnalyzeTracingSession
description: La referencia de la función StopAndAnalyzeTracingSession del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c9bd4a092c22dfcdfb6d463b74207ec11ee6d64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323707"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopAndAnalyzeTracingSession` función detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. A continuación, se inicia inmediatamente una sesión de análisis utilizando el archivo temporal como entrada. Los ejecutables que llamen a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parámetros

*sessionName*\
El nombre de la sesión de seguimiento que se debe detener. Utilice el mismo nombre de sesión que el pasado a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

*numberOfAnalysisPasses*\
El número de pasos de análisis pasa para ejecutarse en el seguimiento. El seguimiento pasa a través del grupo de analizador proporcionado una vez por paso de análisis.

*Estadísticas*\
Puntero a un objeto [TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndAnalyzeTracingSession`escribe estadísticas de recopilación de seguimiento en este objeto antes de devolver.

*analyzerGroup*\
El grupo de analizadores utilizado para el análisis. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de analizadores. Si desea utilizar un grupo de analizadores dinámicos obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero `MakeStaticAnalyzerGroup`entibrelo dentro de un grupo de analizadores estáticos pasando su dirección a .

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
