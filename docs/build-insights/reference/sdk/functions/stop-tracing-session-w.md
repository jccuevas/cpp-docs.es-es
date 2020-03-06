---
title: StopTracingSessionW
description: La C++ referencia de la función STOPTRACINGSESSIONW del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fbb31b600d6aee8c03cb0b52f71c0afcb8b8e3b3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334173"
---
# <a name="stoptracingsessionw"></a>StopTracingSessionW

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `StopTracingSessionW` detiene una sesión de seguimiento en curso y genera un archivo de seguimiento sin procesar. Los archivos de seguimiento sin procesar se pueden pasar a las funciones [Analyze](analyze.md), [AnalzeA](analyze-a.md)y [AnalyzeW](analyze-w.md) para iniciar una sesión de análisis. Los archivos de seguimiento sin procesar también se pueden pasar a las funciones [relog](relog.md), [RelogA](relog-a.md)y [RelogW](relog-w.md) para iniciar la sesión de registro. Los ejecutables que llaman a `StopTracingSessionW` deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StopTracingSessionW(
    const wchar_t*              sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parámetros

*nombresesión*\
Nombre de la sesión de seguimiento que se va a detener. Use el mismo nombre de sesión que el que se pasó a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

\ *outputLogFile*
Ruta de acceso al archivo de registro de salida final donde debe guardarse el seguimiento sin procesar.

*estadísticas*\
Puntero a un objeto de [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopTracingSessionW` escribe estadísticas de la colección de seguimiento en este objeto antes de devolver.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
