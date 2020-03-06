---
title: StartTracingSessionA
description: La C++ referencia de la función STARTTRACINGSESSIONA del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6c5069a2b521472ee4fd06ee313a66de5d7aa814
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334275"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `StartTracingSessionA` inicia una sesión de seguimiento. Los ejecutables que llaman a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parámetros

*nombresesión*\
Nombre de la sesión de seguimiento que se va a iniciar. Use el mismo nombre al llamar a [StopTracingSessionA](stop-tracing-session.md) o a cualquier otra función de seguimiento de detención.

*opciones*\
Puntero a un objeto de [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) . Utilice este objeto para seleccionar los eventos que debe recopilar la sesión de seguimiento.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
