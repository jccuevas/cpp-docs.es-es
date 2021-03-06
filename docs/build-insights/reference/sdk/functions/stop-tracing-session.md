---
title: StopTracingSession
description: La referencia de la función StopTracingSession del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6c7a3c6ca47749491774cc3bcd97aae8aa663ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323523"
---
# <a name="stoptracingsession"></a>StopTracingSession

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopTracingSession` función detiene una sesión de seguimiento en curso y genera un archivo de seguimiento sin procesar. Los archivos de seguimiento sin procesar se pueden pasar a las funciones [Analizar](analyze.md), [AnalzeA](analyze-a.md)y [AnalyzeW](analyze-w.md) para iniciar una sesión de análisis. Los archivos de seguimiento sin procesar también se pueden pasar a las funciones [Relog](relog.md), [RelogA](relog-a.md)y [RelogW](relog-w.md) para iniciar una sesión de recorrección. Las llamadas ejecutables `StopTracingSession` deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
inline RESULT_CODE StopTracingSession(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);

inline RESULT_CODE StopTracingSession(
    const wchar_t*              sessionName
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parámetros

*sessionName*\
El nombre de la sesión de seguimiento que se debe detener. Utilice el mismo nombre de sesión que el pasado a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Ruta de acceso al archivo de registro de salida final donde se debe guardar el seguimiento sin procesar.

*Estadísticas*\
Puntero a un objeto [TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopTracingSession`escribe estadísticas de recopilación de seguimiento en este objeto antes de devolver.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
