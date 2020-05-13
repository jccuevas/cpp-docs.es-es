---
title: StartTracingSessionA
description: La referencia de la función StartTracingSessionA del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c184e214c7f55bb7eaa6eb03f21e792ef90fa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323766"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `StartTracingSessionA` función inicia una sesión de seguimiento. Los ejecutables que llamen a esta función deben tener privilegios de administrador.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parámetros

*sessionName*\
El nombre de la sesión de seguimiento que se ha de iniciar. Utilice el mismo nombre al llamar a [StopTracingSessionA](stop-tracing-session.md) o cualquier otra función de seguimiento de detención.

*Opciones*\
Puntero a un objeto [TRACING_SESSION_OPTIONS.](../other-types/tracing-session-options-struct.md) Utilice este objeto para seleccionar qué eventos debe recopilar la sesión de seguimiento.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
