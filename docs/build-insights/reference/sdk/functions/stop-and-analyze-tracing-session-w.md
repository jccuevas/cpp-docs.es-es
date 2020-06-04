---
title: StopAndAnalyzeTracingSessionw
description: La referencia de la función StopAndAnalyzeTracingSessionW del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2f5f232c3e58c66bc36099d954d97a8f945187ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323716"
---
# <a name="stopandanalyzetracingsessionw"></a>StopAndAnalyzeTracingSessionw

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopAndAnalyzeTracingSessionW` función detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. A continuación, se inicia inmediatamente una sesión de análisis utilizando el archivo temporal como entrada. Los ejecutables que llamen a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionW(
    const wchar_t*              sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parámetros

*sessionName*\
El nombre de la sesión de seguimiento que se debe detener. Utilice el mismo nombre de sesión que el pasado a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

*Estadísticas*\
Puntero a un objeto [TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndAnalyzeTracingSessionW`escribe estadísticas de recopilación de seguimiento en este objeto antes de devolver.

*analysisDescriptor*\
Puntero a un objeto [ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Utilice este objeto para configurar la sesión de análisis iniciada por `StopAndAnalyzeTracingSessionW`.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
