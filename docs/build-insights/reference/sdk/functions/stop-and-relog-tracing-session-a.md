---
title: StopAndRelogTracingSessionA
description: La C++ referencia de la función STOPANDRELOGTRACINGSESSIONA del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c9fe2ea47b378565d3ce9785b6f4cc3e541ebe80
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334299"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `StopAndRelogTracingSessionA` detiene una sesión de seguimiento en curso y guarda el seguimiento resultante en un archivo temporal. Una sesión de registro se inicia inmediatamente mediante el archivo temporal como una entrada. El último seguimiento reiniciado por la sesión de registro se guarda en un archivo especificado por el autor de la llamada. Los ejecutables que llaman a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parámetros

*nombresesión*\
Nombre de la sesión de seguimiento que se va a detener. Use el mismo nombre de sesión que el que se pasó a [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)o [StartTracingSessionW](start-tracing-session-w.md).

\ *outputLogFile*
Archivo en el que se va a escribir el seguimiento reiniciado por la sesión de registro.

*estadísticas*\
Puntero a un objeto de [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndRelogTracingSessionA` escribe estadísticas de la colección de seguimiento en este objeto antes de devolver.

\ *analysisDescriptor*
Puntero a un objeto de [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Utilice este objeto para configurar la sesión de reinicio de sesión iniciada por `StopAndRelogTracingSessionA`.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
