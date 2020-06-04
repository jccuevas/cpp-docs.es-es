---
title: estructura TRACING_SESSION_OPTIONS
description: El SDK de C++ Build Insights TRACING_SESSION_OPTIONS referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aeb6299aea8dc0661b9469ee524e7aa4d010aca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323430"
---
# <a name="tracing_session_options-structure"></a>estructura TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRACING_SESSION_OPTIONS` estructura se utiliza al inicializar una [estructura ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Describe qué eventos capturar durante la colección de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `SystemEventFlags` | Una máscara de bits que describe los eventos del sistema que se han de capturar. Para obtener más información, consulte [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Una máscara de bits que describe los eventos MSVC que se han de capturar. Para obtener más información, consulte [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
