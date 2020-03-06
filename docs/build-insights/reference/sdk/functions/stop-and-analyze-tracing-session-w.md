---
title: StopAndAnalyzeTracingSessionW
description: La C++ referencia de la función STOPANDANALYZETRACINGSESSIONW del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec36162efcd2bfcf17cb07a997a7ff170338d3d2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334269"
---
# <a name="stopandanalyzetracingsessionw"></a>StopAndAnalyzeTracingSessionW

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `StopAndAnalyzeTracingSessionW` detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. Una sesión de análisis se inicia inmediatamente utilizando el archivo temporal como una entrada. Los ejecutables que llaman a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionW(
    const wchar_t*              sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parámetros

*nombresesión*\
Nombre de la sesión de seguimiento que se va a detener. Use el mismo nombre de sesión que el que se pasó a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

*estadísticas*\
Puntero a un objeto de [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndAnalyzeTracingSessionW` escribe estadísticas de la colección de seguimiento en este objeto antes de devolver.

\ *analysisDescriptor*
Puntero a un objeto [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Utilice este objeto para configurar la sesión de análisis iniciada por `StopAndAnalyzeTracingSessionW`.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
